# Un
Invoke `:Copilot setup` to authenticate and enable GitHub Copilot.

Suggestions are displayed inline and can be accepted by pressing <Tab>.  If
inline suggestions do not appear to be working, invoke `:Copilot status` to
verify Copilot is enabled and not experiencing any issues.

COMMANDS                                        *:Copilot*

                                                *:Copilot_disable*
:Copilot disable        Globally disable GitHub Copilot inline suggestions.

                                                *:Copilot_enable*
:Copilot enable         Re-enable GitHub Copilot after :Copilot disable.

                                                *:Copilot_setup*
:Copilot setup          Authenticate and enable GitHub Copilot.

                                                *:Copilot_signout*
:Copilot signout        Sign out of GitHub Copilot.

                                                *:Copilot_status*
:Copilot status         Check if GitHub Copilot is operational for the current
                        buffer and report on any issues.

                                                *:Copilot_model*
:Copilot model          If a preview or other alternate model for completions
                        is available, provides an interactive interface for
                        enabling it for the rest of the current Vim/Neovim
                        session.  Note that typically the number of available
                        completions models is one, rendering this command
                        inert.

                                                *:Copilot_panel*
:Copilot panel          Open a window with up to 10 completions for the
                        current buffer.  Use <CR> to accept a completion.
                        Maps are also provided for [[ and ]] to jump from
                        completion to completion.

                                                *:Copilot_version*
:Copilot version        Show version information.

                                                *:Copilot_upgrade*
:Copilot upgrade        Upgrade the Copilot Language Server to the latest
                        version with `npx`.  This works by temporarily setting
                        |g:copilot_version| to "latest" and restarting.

Aber auch bei setup exit with 190titled 2

