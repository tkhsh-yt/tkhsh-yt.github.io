## TODO 基本的な設定
ここでは，Emacs を使っている多くの人が行っているであろう基本的な設定をする．  
つまり，追加でダウンロードしたパッケージに関する設定ではなく，Emacs 本体のみに対して適用される設定についてのみ触れる．  
既に少しだけ書いているが，Emacs の設定は Emacs Lisp と呼ばれる Lisp の方言の一つを用いて行う．  

以下のコードを初期化ファイルに追加で記述する．

```elisp
;; 起動時にメッセージを表示しないようにする
(setq inhibit-start-up-messege t)

;; 言語を日本語にする
(set-language-environment 'Japanese)
  
;; UTF-8
(set-default 'buffer-file-coding-system 'utf-8-with-signature)
(prefer-coding-system 'utf-8)

;; ツールバーの非表示
(tool-bar-mode 0)
  
;; メニューバーの非表示
(menu-bar-mode 0)

;; ダイアログを使わないようにする
(setq use-dialog-box nil)

;; 対応する括弧を強調する
(show-paren-mode t)

;; 現在行を目立たせる
(global-hl-line-mode t)

;; 行番号を表示する
(global-linum-mode t)

;; スクロールバーの非表示
(scroll-bar-mode 0)

;; yes/no ではなく y/n
(defalias 'yes-or-no-p 'y-or-n-p)

;; ビープ音，フラッシュを消す
(setq ring-bell-function 'ignore)

;; C-h で一文字前を消す
(define-key key-translation-map (kbd "C-h") (kbd "<DEL>"))

;; スクロールを 1 行ごとにする
(setq scroll-conservatively 1)

;; バックアップファイルを作らない（お好み）
(setq make-backup-files nil)

;; 終了時にオートセーブファイルの削除
(setq delete-auto-save-files t)

;; ウィンドウを透過する
;; (アクティブ/非アクティブ)時の透過度
(add-to-lisp 'default-frame-alist '(alpha . (0.8, 0.8))
```

この辺は多分，多くの人が設定していると思う．  
このサイトでは，後に helm と呼ばれる Emacs に統一的なインターフェースを提供するパッケージを紹介する．  
そのため，以下の設定はいらなくなると思うが，helm を使わない人もいると思うので，紹介しておく．  

```elisp
;; 検索時に大文字，小文字を区別しない
(setq case-fold-search t)

;; インクリメンタルサーチ時に大文字，小文字を区別しない
(setq isearch-case-fold-search t)

;; バッファー名検索で大文字，小文字を区別しない
(setq read-buffer-completion-ignore-case t)

;; ファイル名検索で大文字，小文字を区別しない
(setq read-file-name-completion-ignore-cast t)
```

他にもおすすめの設定が沢山あると思うが，ここではこの辺にしておく．  
この設定はしておいた方がいいというものがあったらプルリクを送って貰えると助かります．

## 参考

- [プログラマーズ雑記帳 - Emacs の検索、置換における大文字小文字の区別の切り替え](http://yohshiy.blog.fc2.com/blog-entry-191.html)
