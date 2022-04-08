# type: ignore
# pylint: disable-all

import os

ACTIVATE_VENV = "./venv/bin/activate"
DEFAULT_CONFIG_PATH = "~/Development/github/dotfiles_v2/dotfiles/general/qtile/config.py"
DEFAULT_LOG_LEVEL = "DEBUG"

def phony_target(target: str, action: str, env=None):
    if not env:
        env = Environment(ENV=os.environ)
    return env.AlwaysBuild(env.Alias(target, [], action))

cf = ARGUMENTS.get("cf", DEFAULT_CONFIG_PATH)
ll = ARGUMENTS.get("ll", DEFAULT_LOG_LEVEL)

a_test_config = f"""
. {ACTIVATE_VENV}
LOG_LEVEL={ll} ./scripts/xephyr -c {cf}
"""

phony_target("test-config", a_test_config)


a_help = f"""
@echo Base Commands:
@echo test-config [cf={DEFAULT_CONFIG_PATH}] [ll={DEFAULT_LOG_LEVEL}]
@echo
"""
Default(phony_target("help", a_help))
