```
younhee/
├── docs/
│   ├── overview.md           # General architecture description and workflows
│   ├── setup.md              # Installation guide, environment setup and deployment
│   └── api.md                # API documentation (if applicable)
│
├── configs/
│   ├── default.yaml          # Default parameters (ports, thresholds, timings)
│   ├── logging.yaml          # Logging configuration (levels, formats, handlers)
│   └── development.yaml      # Development-specific overrides
│
├── src/
│   ├── __init__.py
│   ├── app.py                # Entry point: starts application and main loop
│   │
│   ├── controller/
│   │   ├── __init__.py
│   │   └── arduino.py        # Serial client to send commands to Arduino
│   │
│   ├── vision/
│   │   ├── __init__.py
│   │   ├── capture.py        # Captures frames from iPhone stream
│   │   ├── preprocess.py     # Image transformations and resizing
│   │   └── infer.py          # Inference logic with movement detection model
│   │
│   ├── sound/
│   │   ├── __init__.py
│   │   └── player.py         # Playback of "green light/red light" sounds
│   │
│   ├── state_machine.py      # Defines "GREEN → wait → RED → check → ..." flow
│   └── utils.py              # Helper functions (config loader, logger, timing)
│
├── assets/
│   ├── sounds/
│   │   ├── green_light.mp3   # Green light sound effect
│   │   ├── red_light.mp3     # Red light sound effect
│   │   └── game_over.mp3     # Game over sound (optional)
│   │
│   └── models/
│       ├── movement_model.onnx    # Movement detection model (ONNX/PyTorch exported)
│       └── model_metadata.json   # Model version, input/output specs
│
├── scripts/
│   ├── run_local.sh          # Script to run locally (venv + app.py)
│   ├── build_docker.sh       # Script to build Docker image
│   ├── setup_env.sh          # Environment setup script
│   └── calibrate.py          # Camera/model calibration script
│
├── tests/
│   ├── __init__.py
│   ├── test_arduino.py       # Serial mocks: command sending tests
│   ├── test_infer.py         # Unit tests for inference (mock frames)
│   ├── test_state_machine.py # State transition validation
│   ├── test_vision.py        # Vision pipeline tests
│   ├── test_sound.py         # Sound playback tests
│   └── test_app.py           # High-level integration test (no real hardware)
│
├── .gitignore                # Ignore /venv, __pycache__, .env, etc.
├── .env.example              # Environment variables template
├── Dockerfile                # Image to run src/app.py with full stack
├── docker-compose.yml        # Multi-container setup (if needed)
├── requirements.txt          # Python dependencies (opencv-python, pyyaml, pyserial, onnxruntime)
├── requirements-dev.txt      # Development dependencies (pytest, black, flake8)
├── Makefile                  # Tasks: install, lint, format, test, docker
├── pyproject.toml            # Python project configuration (if using modern tools)
└── README.md                 # Project summary, quick usage and roadmap
```

