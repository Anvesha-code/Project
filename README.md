mock_state = MagicMock()
mock_state.error_message = None
mock_state.input_type = "swagger"
mock_state.request_id = "123"
mock_state.state_id = "state123"
mock_state.framework = "pytest"
mock_state.swagger_url = "http://test"
mock_state.url_validation_passed = True
mock_state.swagger_schema_validation_passed = True
mock_state.prompt_text_validation_passed = True
mock_state.prompt_validation_results = ""
mock_state.prompt_text = "prompt"
mock_state.generated_code = "code"
mock_state.generated_code_status = "success"
mock_state.code_validation_result = {}
mock_state.llm_trace = "trace"

# ✅ KEEP this line — just assign mock_state instead of dict
mock_controller.return_value.run.return_value = mock_stat
