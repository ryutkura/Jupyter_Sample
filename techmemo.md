# 仮想環境の作成と管理に関するTech Memo

## 1. 仮想環境の作成方法
### 仮想環境の命名方法
仮想環境の名前は任意ですが、プロジェクトに関連する名前を付けると管理がしやすくなります。

### 仮想環境の作成手順
1. **Pythonのインストール**:
   まず、Pythonがインストールされていることを確認します。インストールされていない場合は、[Pythonの公式サイト](https://www.python.org/)からインストールしてください。

2. **仮想環境の作成**:
   プロジェクトのディレクトリに移動し、仮想環境を作成します。
   ```bash
   python -m venv myenv
   ```
   ここで、`myenv`は仮想環境の名前です。任意の名前を付けることができます。

3. **仮想環境の有効化**:
   - Windows:
     ```bash
     myenv\Scripts\activate
     ```
   - macOS/Linux:
     ```bash
     source myenv/bin/activate
     ```

## 2. ライブラリのインストール
### `requirements.txt`ファイルの作成
1. **仮想環境を有効化**:
   ```bash
   myenv\Scripts\activate  # Windows
   source myenv/bin/activate  # macOS/Linux
   ```

2. **インストールされているライブラリのリストを作成**:
   ```bash
   pip freeze > requirements.txt
   ```
   このコマンドは、現在の仮想環境にインストールされているすべてのライブラリとそのバージョンをリスト化し、`requirements.txt`ファイルに書き出します。これにより、他の環境でも同じライブラリを簡単にインストールすることができます。

### `requirements.txt`ファイルの反映方法
1. **仮想環境を有効化**:
   ```bash
   myenv\Scripts\activate  # Windows
   source myenv/bin/activate  # macOS/Linux
   ```

2. **ライブラリのインストール**:
   ```bash
   pip install -r requirements.txt
   ```
   このコマンドは、`requirements.txt`ファイルに記載されているすべてのライブラリをインストールします。

## 3. 仮想環境のカーネルのインストール
### 詳細な手順
1. **仮想環境の有効化**:
   ```bash
   myenv\Scripts\activate  # Windows
   source myenv/bin/activate  # macOS/Linux
   ```

2. **Jupyter Notebookのインストール**:
   仮想環境内でJupyter Notebookをインストールします。
   ```bash
   pip install jupyter
   ```

3. **IPythonカーネルのインストール**:
   仮想環境をJupyter Notebookのカーネルとして認識させるために、IPythonカーネルをインストールします。
   ```bash
   pip install ipykernel
   python -m ipykernel install --user --name myenv --display-name "Python (myenv)"
   ```
   - `--name`オプションは、カーネルの内部名を指定します。これは仮想環境の名前と一致させると管理がしやすくなります。
   - `--display-name`オプションは、Jupyter Notebookのカーネルリストに表示される名前を指定します。任意の名前を付けることができます。

4. **Jupyter Notebookの起動**:
   仮想環境内でJupyter Notebookを起動します。
   ```bash
   jupyter notebook
   ```

5. **カーネルの選択**:
   Jupyter Notebookのインターフェースが開いたら、新しいノートブックを作成し、上部の「Kernel」メニューから「Change kernel」を選択し、先ほど作成した「Python (myenv)」を選択します。

## 4. 仮想環境を作成できる言語と仮想環境を構築するメリット
### 仮想環境を作成できる言語
- **Python**: `venv`, `virtualenv`
- **Node.js (JavaScript)**: `nvm`, `npm`, `yarn`
- **Ruby**: `rbenv`, `RVM`, `Bundler`
- **Java**: `SDKMAN!`, `Maven`, `Gradle`
- **PHP**: `Composer`
- **Go**: `Go Modules`
- **Rust**: `Cargo`

### 仮想環境を構築するメリット
- **依存関係の分離**: プロジェクトごとに異なるライブラリやバージョンを使用できるため、依存関係の衝突を避けることができます。
- **環境の再現性**: `requirements.txt`ファイルを使用することで、他の開発者や別の環境でも同じ設定を再現することができます。
- **クリーンな開発環境**: グローバル環境を汚さずに、プロジェクトごとにクリーンな開発環境を維持できます。
