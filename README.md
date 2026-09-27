# Tweetbar

Tweetbar is a Django app for sharing short posts and photos. Visitors can browse and search the feed; registered users can create, edit, and delete their own posts.

## Requirements

- Python compatible with the versions pinned in `requirements.txt`
- PowerShell on Windows

## Set Up

Run these commands from the repository root, the folder containing `requirements.txt`:

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r .\requirements.txt
python .\chaiheadq\manage.py migrate
```

If PowerShell does not allow virtual-environment activation, run the project commands with `.\.venv\Scripts\python.exe` instead of `python`.

## Run Locally

From the repository root:

```powershell
python .\chaiheadq\manage.py runserver
```

Open <http://127.0.0.1:8000/>. The tweet feed is available at <http://127.0.0.1:8000/tweet/list/>.

## Use Tweetbar

- Browse the feed without signing in.
- Search posts by their text or the author's username.
- Select **Join** or **Create an account** to register. After successful registration, Tweetbar takes you to the login page and confirms that your account was created.
- Log in to create posts, attach photos, or edit and delete your own posts.
- Use **Log out** in the navigation bar to end your session.

Authentication pages:

- Registration: `/accounts/register/`
- Login: `/accounts/login/`
- Logout: available from the navigation bar

Uploaded photos are stored under `chaiheadq/media/photos/` during development. Pillow is included in `requirements.txt` because Django uses it to process image uploads.

## Check the Project

```powershell
python .\chaiheadq\manage.py check
python .\chaiheadq\manage.py test
```

If Django reports that Pillow is missing, confirm that the same virtual environment is used for both installation and `runserver`, then install the requirements again:

```powershell
python -m pip install -r .\requirements.txt
```

## Deployment Note

The current settings are for local development. Before deploying, configure a private `SECRET_KEY`, disable `DEBUG`, set `ALLOWED_HOSTS`, and configure production static-file and media storage.