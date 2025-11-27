import sys
import os

# Get project root path (folder where app/ and tests/ live)
PROJECT_ROOT = os.path.dirname(os.path.dirname(os.path.abspath(__file__)))

# Add project root to Python path so pytest can find "app"
sys.path.insert(0, PROJECT_ROOT)
