

habitrpg.el
===============

Quick hack to integrate org-mode and habitrpg. Very much a work in progress. Triggers after a TODO state change in org-mode (so you need to have an intermediary stage between TODO and DONE, like NEXT, or just give habitrpg-add a keybinding).

Tag (in org-mode) your habits and dailys with `hrpghabit`, `hrpgdaily`, and `hrpgreward` to get them in the right category.

Installation
------------

Add to your .emacs:

    (setq habitrpg-api-user "ID HERE")
    (setq habitrpg-api-token "TOKEN HERE")

Add these hooks if you want it to trigger after a state change, otherwise just add keybindings for them instead.

	(add-hook 'org-after-todo-state-change-hook 'habitrpg-add)
	(add-hook 'org-after-todo-state-change-hook 'habitrpg-done 'append)

-------------------------------------------------------------------------------

If you want to use the clocking feature:

	(add-hook 'org-clock-in-hook 'habitrpg-clock-in)
	(add-hook 'org-clock-out-hook 'habitrpg-clock-out)

and set the variable `hrpg-tags-list` to the habits you want to associate with the clocked task.

    (add-to-list 'hrpg-tags-list "PROGRAMMING")
    (add-to-list 'hrpg-tags-list "WORK")

Then your habit will get upvoted every two minutes.
