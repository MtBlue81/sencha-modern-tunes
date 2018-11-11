# ModernTunes application

[サンプル](https://mtblue81.github.io/sencha-modern-tunes/build/production/ModernTunes/)
## Quick start (雛形作成まで)
1. private npm 登録  
  [Sign in to MyGet - MyGet - Hosting your NuGet, npm, Bower, Maven, PHP Composer and Vsix packages](https://sencha.myget.org/)

2. npm login
  ```
  npm login --registry=https://sencha.myget.org/F/community/npm/ --scope=@sencha

  ``````
3. ジェネレータインストール
  ```
  npm install -g @sencha/ext-gen 
  ```

4. Quick start  
  SDK, CMD とかがインストールされる.  
  インタラクティブなアプリ情報設定.  
  変更したもの
  - プロジェクト名
  - template -> moderndesktopminimal
  ```
  ext-gen app -i
  ```
  
5. 起動
  ```
  cd modern-tunes;
  npm start
  ```
  developmentでビルド
  http://localhostjjj:1962/ で起動

  ### わかること
  詳細は [What's All That Stuff? \| Ext JS 6.6.0-CE](https://docs.sencha.com/extjs/6.6.0-CE/guides/quick_start/Set_Up_Start_Coding_the_App/Whats_All_That_Stuff.html) に書いてある.
  
  大事なのはView,ViewController,ViewModelが連携していること.(MVVM)
  #### View
  - UIを表すコンポーネントを定義,配置する.
  #### ViewController
  - 関連するViewについてのビジネスロジック(というかハンドラなどのUIロジック)を定義する.
  #### ViewModel
  - 関連するViewに紐付くデータ(およびStore)を定義する.
  
  #### その他
  - landingページは `app.js`の`name`コンフィグで指定されている`app/desktop/src/Application.js`
  - launchコンフィグでViewportに `app/desktop/src/view/main/MainView.js`を追加している.
  - watchオプションが効いてるので修正後画面が自動反映される.
  - MainView.scss 変更は効かない・・？
  - MainView.js,MainViewController.js,MainViewModel.jsが組になっている.
  - ViewControllerは Viewの`controller`に設定することで、ViewのhandlerがViewControllerのメソッドに連結される. (MainView内のbuttonを参照)
    - 設定する値はViewController側の`alias`指定したもの.
  - ViewModelとの接続はViewの`viewModel`に設定できる.
    - items内でVieｗModelの値と `bind`コンフィグを使って連動させられる. (たぶん双方向バインディング)
  - itemsではxtypeによるコンポーネントのエイリアスを使った指定が可能. (遅延インスタンス化ができるメリットあり)
  - itemsに`reference`コンフィグを指定することで、ViewControllerから `lookupReference` による参照取得が可能となる.
