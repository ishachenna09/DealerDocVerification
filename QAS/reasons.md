## in app/config.py

Tech explanation: why Pydantic Settings instead of os.getenv() everywhere

```os.getenv("PORT") returns a string or None — no validation, no type conversion, and if you forget to set it in .env, you get a silent None that blows up somewhere deep in your code with a confusing error. pydantic-settings validates on startup: if access_token_expire_minutes isn't a valid int, or a required variable is missing, your app fails immediately at boot with a clear error — not three requests later during a login attempt. This is the same "fail fast" principle behind why Pydantic is used for request validation too.```