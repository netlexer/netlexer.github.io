---
layout: page
title: Hello Emacs World!
tagline: Supporting tagline
---
{% include JB/setup %}

## Easy Menu Navigation of init.el

Here is a useful way to navigate your `init.el` by means of a simple
menu. My emacs init is nearly 1000 lines, split into convenient
sections by easily parsed section headers, like this

```elisp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;; Startup routines
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
```

The following elisp snippet uses a regular expression wrapped inside an
emacs-lisp-mode-hook to create a simple menu from all such headers

```elisp
;; Create a menu from matched section headers in this file. Bound to C-f6.
;; Alternatively, M-S-down-mouse-3 invokes a mouse menu. 
(add-hook 'emacs-lisp-mode-hook
          (lambda ()
            (when (string= (buffer-name) "init.el")
              (setq imenu-generic-expression
                    '((nil "^;\\{70,\\}\n;;; \\(.+\\)" 1))))))

(global-set-key [(control f6)] 'imenu)
```

The regular expression matches a sequence of 70 or more `;`
characters, a newline, another three comment characters, and a space
followed by a descriptive section header, which gets added to the
menu. 

Read [My Emacs init.el](https://github.com/netlexer/dot.emacs.d/) for
further ideas. 

