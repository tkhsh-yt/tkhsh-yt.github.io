## El-Get
El-Get は Cask が Python に依存しているのに対して Emacs Lisp のみで実装されている．  
El-Get の詳しい説明については，[貳佰伍拾陸夜日記 - Cask はもう古い、これからは El-Get - いまどきの Emacs パッケージ管理](http://tarao.hatenablog.com/entry/20150221/1424518030) を参考にするのがよい．

また，そのサイトで言われているように Cask から El-Get への移行は簡単に行える．   
Github の [el-get](https://github.com/dimitri/el-get) の README.md を参考にしつつ，パッケージをインストールするまでの流れを説明する．

### インストール
   `~/.emacs.d/init.el` に以下のコードを追加する．
   
   ```elisp
   (add-to-list 'load-path "~/.emacs.d/el-get/el-get")

   (unless (require 'el-get nil 'noerror)
     (with-current-buffer
       (url-retrieve-synchronously
         "https://raw.githubusercontent.com/dimitri/el-get/master/el-get-install.el")
       (goto-char (point-max))
       (eval-print-last-sexp)))

       (add-to-list 'el-get-recipe-path "~/.emacs.d/el-get-user/recipes")
       (el-get 'sync)
   ```
   
   El-Get のインストールに必要なことはこれだけである．  
   このコードを追加後，式を評価するか，Emacs を再起動すれば勝手に El-Get をインストールしてくれる．
   
### パッケージの指定
   El-Get でインストールするパッケージを指定する方法は，

   ```elisp
   (el-get-bundle package-name)
   ```
   
   と `~/.emacs.d/init.el` に追加するだけである．

   例えば，magit をインストールしたいときには，

   ```elisp
   (el-get-bundle magit)
   ```
   
   と書く． Github からパッケージをインストールしたい場合には `所有者/リポジトリ` の形で指定する．

   ```elisp
   (el-get-bundle fnwiya/hatena-blog-mode)
   ```

   また，配布元を指定する場合には，

   ```elisp
   (el-get-bundle elpa:org)
   ```

   のように書く．  
   この他にも様々なオプションがあるが，最初に挙げたブログの記事を読むといいと思います．  
   また，インストールされているパッケージのバージョンを固定するための機能もあり，アップデートしたら環境が壊れたという場合でもある程度対処することができるようになります（？）．  
   （この機能は使ったことがないので，どの程度上手く機能するのか自分はわかりません．)

### 基本的な使い方
   - `M-x el-get-install`  
     パッケージ名を指定してインストール．
   - `M-x el-get remove`  
     インストール済みパッケージの名前を指定してパッケージの削除．
   - `M-x el-get-reinstall`  
     インストール済みパッケージの再インストール．
   - `M-x el-get-self-update`  
     El-Get 自身のアップデート．
   - `M-x el-get-update`  
     インストール済みのパッケージ名を指定して更新．
   - `M-x el-get-update-all`  
     インストール済みの全てのパッケージを更新．
   - `M-x el-get-list-packages`  
     インストール可能なパッケージのリストを表示．

### パッケージの設定
   El-Get にはインストールしたパッケージに対する設定をわかりやすく管理するための機能があります．  
   まだ，パッケージの設定について話していないため，これについては後で書きます．
