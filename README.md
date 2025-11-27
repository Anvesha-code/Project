# tests/test_script_generation.py
import pytest
from fastapi import FastAPI
from fastapi.testclient import TestClient
from unittest.mock import patch, MagicMock
import importlib

# 1️⃣ Auto-mock all dependencies before router import happens
@pytest.fixture(autouse=True)
def mock_dependencies():
    with patch('app.api.v1.routes.testscript_generation_service.get_config') as mock_get_config, \
         patch('app.api.v1.routes.testscript_generation_service.Controller') as mock_controller:

        mock_get_config.return_value = {"APP_ENV": "test"}
        mock_controller.return_value.run.return_value = {"status": "ok"}

        yield


# 2️⃣ Create test FastAPI app and load router lazily
@pytest.fixture()
def client():
    module = importlib.import_module('app.api.v1.routes.testscript_generation_service')
    router = module.router

    app = FastAPI()
    app.include_router(router)

    return TestClient(app)
