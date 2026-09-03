# Agent Loop: Learning Project

## Create virtual environment, activate and install dependencies
```bash
uv init
uv python install 3.12
uv python pin 3.12

uv add -r requirements.txt
```

## To update dependencies
```bash
uv sync
```

## Run FastAPI App
```bash
uv run python -m agent_loop.app
```

## Reference
[Loop Engineering And Harness Engineering Crash Course](https://www.youtube.com/watch?v=3uO6V05LBjU)