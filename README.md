# fail2ban-ntfy-action

## How to
To use NTFY as a default action:
- Copy `ntfy.conf` to `/etc/fail2ban/action.d/ntfy.conf`
- Modify the `/etc/fail2ban/jail.local` like so:
    - Comment out the line `action = %(action_)s`
    - Under it add:

    ```
    action_ntfy = %(action_)s
                ntfy[name="%(__name__)s", ntfyurl="https://ntfy.sh/YOUR_NTFY_TOPIC", apitoken="YOUR_NTFY_API_TOKEN"]
    action = %(action_ntfy)s
    ```
