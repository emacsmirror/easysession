# easysession - Changelog

URL: https://github.com/jamescherti/easysession.el
Author: [James Cherti](https://www.jamescherti.com/)

## 1.1.4

* Add macros to simplify the definition of load/save handlers, enabling users to create custom handlers and extend EasySession more easily
* Optimize EasySession functions to improve the performance of session loading and saving operations.
* Contribution by Artem Tseranu: Allow excluding the current session when switching sessions
* Rename session prompts to include the current session name
* Update `.github` files, docstrings, and GitHub Actions
* Improve session saving by making `write-region` more efficient and reliable for file output.
* Enhance how the session file is read from disk
* Fix `easysession-save-as` `(interactive)` form and update rename session to include the session name in the prompt
* Add a `.nosearch` file to the `tests/` directory
* Add `CHANGELOG.md`

## 1.1.3

* Enhance and refactor the source code
* Improve session loading and saving
* Enhance unit tests
* Replace the `f` package with built-in functions to reduce dependencies
* Fix: Adjust settings to ensure EasySession restores all frames
* Fix: Prevent the Dirvish package from breaking the session file
* Fix: Refactor frameset filtering into a dedicated function
* Fix: `lsp-ui-doc`: Failed to evaluate session information
* Add option to exclude specific functions from `find-file-hook` when restoring a file
* Replace `(dired-current-directory)` with `default-directory`
* Add variable: `easysession-frameset-restore-geometry`
* Ensure `easysession-load` sets `easysession--load-error` to `t` on failure
* Remove direct `require` and replace it with `default-directory`
* Add function: `easysession-path`
* Rename functions and variables such (`easysession--is-loading`, `easysession-get-session-name`, `easysession-get-session-file-path`)
* Enhance functions to get session file path and session name

## 1.1.2

* Ensure access to frames during the Emacs shutdown process
* Enable `tab-bar-mode` if the loaded session includes a `tab-bar`
* Removed reliance on `kill-emacs-hook` for cleanup, as frames were no longer accessible at that stage.
* Add a check to save handlers
* Add an error message when the handler type is not a function

## 1.1.1

* Refactor the load indirect buffers function: simplify logic and improve readability
* Enhance restoring frameset (customizable and disabled when running as a daemon)
* Contribution by Enzo Gurgel: Display the session name in the mode lighter.
* Make easysession functions utilize the `session-name` argument
* Make unit tests delete the test session
* Make `easysession-save-as` ask the user to enter a session when `session-name` is not specified
* Make `easysession-delete` return `t` when the session is successfully deleted
* Remove docstring warning
* Add autoload to interactive functions
* Add easysession-frameset-restore-force-display, easysession-frameset-restore-force-onscreen, additional frameset-restore options, easysession-frameset-restore-cleanup-frames, easysession-frameset-restore-reuse-frames
* Change the default value of `easysession-frameset-restore-force-onscreen` to `(display-graphic-p)`
* Ensure handlers return a non-nil value

## 1.1.0

* Implement handlers allowing EasySession to become extensible. It allows users to add their own handlers that can include entries in the session file.
* Fix: Fontify buffers when `redisplay-skip-fontification-on-input` is non-nil
* Create unit tests for EasySession using GitHub Actions and Cask
* Add predicate that determines if the session is saved automatically
* Update docstrings
* Renames `easysession-set-current-session` to `easysession--set-current-session`.
* Change lighter to EasySes
* Ignore `jit-lock-fontify-now` errors

## 1.0.5

* Fix issue that prevented EasySession from saving/loading frame geometry
* Use `bound-and-true-p` to check if `easysession--load-geometry` is set to `t`
* Add a defcustom containing a function to retrieve buffers for persistence and restoration
* Fix warnings
* Add `:nowarn` to `find-file-noselect`

## 1.0.4

* Optimize loading file editing buffers and indirect buffers
* Improve detection of indirect buffers
* Improve error handling and messages
* Enhance `easysession-set-current-session` session name check
* Ensure `easysession--handler-load-base-buffers` loads base buffers
* Fix: Ensure indirect buffer names match frameset buffer names
* Fix: Add the `easysession-quiet` defcustom
* Simplify the `easysession--handler-load-base-buffers` function
* Add `easysession-before-save-hook` and `easysession-after-save-hook`
* Add `:group` to `easysession-save-interval` and rename `easysession-timer` to `easysession--timer`
* Make easysession use `frameset-persistent-filter-alist` instead of `frameset-filter-alist`
* Make `easysession--init-frame-parameters-filters` parameter mandatory
* Fix `frameset-filter-alist` bug and improve session reading
* Rename variables (`easysession--is-valid-session-name` and `easysession-after-new-session-created-hook`)

## 1.0.3

* Handle frameset and buffer errors when loading a session, and update README.md
* Add `auto-save-interval` and `easysession--load-geometry`
* Correct `easysession-save-interval` variable name
* Add the `easysession--is-loading-p` variable
* Remove `interactive` from `easysession-load-including-geometry`
* Fix warnings

## 1.0.2

* New feature: save/load geometry
* Add the `easysession-rename` function
* Fix the `make-directory` error when a file's parent directory is missing
* Fix issue with `frameset-restore` caused by a change in the file format
* Fix error: Cannot open load file: No such file or directory: f
* Add new options, variables, and functions: `easysession-persist-geometry`, `easysession--get-geometry-frameset-filter-alist`, `frameset--text-pixel-width`, `frameset--text-pixel-height`, and `easysession-load-including-geometry`
* Fix warning: `called-interactively-p` called with 0 arguments but requires 1
* Fix warning: unused lexical argument `session-name`

## 1.0.1

* Fix border color and border width issues
* Add support for indirect buffers
* Rename variables and update comments
* Add list of geometry parameters
* Fix warnings
* Optimization: Decrease the frequency of calls to `easysession--init-frame-parameters-filters` to improve efficiency.

## 1.0.0

* Initial version of EasySession
* Add docstrings
* Add `easysession-mode`
* Add additional hooks
* Remove the `emacs-startup-hook` function
* Fix warning: the function `dired-current-directory` is not known to be defined
