# type: ignore
# pylint: disable-all

import os

ACTIVATE_VENV = "./venv/bin/activate"
DEFAULT_CONFIG_PATH = "~/Development/github/dotfiles_v2/dotfiles/general/qtile/config.py"
DEFAULT_LOG_LEVEL = "DEBUG"
DEFAULT_SCREEN_SIZE = "800x600"

def phony_target(target: str, action: str, env=None):
    if not env:
        env = Environment(ENV=os.environ)
    return env.AlwaysBuild(env.Alias(target, [], action))

ss = ARGUMENTS.get("ss", DEFAULT_SCREEN_SIZE)
cf = ARGUMENTS.get("cf", DEFAULT_CONFIG_PATH)
ll = ARGUMENTS.get("ll", DEFAULT_LOG_LEVEL)

a_test_config = f"""
. {ACTIVATE_VENV}
LOG_LEVEL={ll} SCREEN_SIZE={ss} ./scripts/xephyr -c {cf}
"""

a_test_config_multiple = f"""
. {ACTIVATE_VENV}
LOG_LEVEL={ll} SCREEN_SIZE={ss} ./scripts/xephyr-multiple -c {cf}
"""

phony_target("test-config", a_test_config)
phony_target("test-config-multiple", a_test_config_multiple)


a_help = f"""
@echo Base Commands:
@echo test-config [cf={DEFAULT_CONFIG_PATH}] [ll={DEFAULT_LOG_LEVEL}] [ss={DEFAULT_SCREEN_SIZE}]
@echo test-config-multiple [cf={DEFAULT_CONFIG_PATH}] [ll={DEFAULT_LOG_LEVEL}] [ss={DEFAULT_SCREEN_SIZE}]
@echo
"""
Default(phony_target("help", a_help))
