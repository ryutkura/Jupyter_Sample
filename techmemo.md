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

## カーネルの更新手順
カーネルの更新（ライブラリの更新）を行うためには、以下の手順を実行します。

### 手順

1. **仮想環境の有効化**:
   まず、仮想環境を有効化します。
   - Windows:
     ```bash
     hogehoge\Scripts\activate
     ```
   - macOS/Linux:
     ```bash
     source hogehoge/bin/activate
     ```

2. **新しいライブラリのインストール**:
   仮想環境内で新しいライブラリをインストールします。
   ```bash
   pip install new_library
   ```

3. **`requirements.txt`ファイルの更新**:
   現在の仮想環境にインストールされているすべてのライブラリをリスト化し、`requirements.txt`ファイルを更新します。
   ```bash
   pip freeze > requirements.txt
   ```

4. **IPythonカーネルの再インストール**:
   仮想環境をJupyter Notebookのカーネルとして再登録します。
   ```bash
   python -m ipykernel install --user --name hogehoge --display-name "Python (hogehoge)"
   ```

### まとめ
- 仮想環境を有効化し、新しいライブラリをインストールする。
- `pip freeze > requirements.txt`コマンドを実行して`requirements.txt`ファイルを更新する。
- IPythonカーネルを再インストールして、Jupyter Notebookのカーネルとして再登録する。


## カーネルの更新に伴う名前の変更について
はい、カーネルの名前や表示名を変更しても問題ありません。`--name`オプションと`--display-name`オプションはそれぞれ以下のような役割を持っています：

- **`--name`**: カーネルの内部名を指定します。これは仮想環境の名前と一致させると管理がしやすくなりますが、必ずしも一致させる必要はありません。
- **`--display-name`**: Jupyter Notebookのカーネルリストに表示される名前を指定します。任意の名前を付けることができます。

例えば、以下のように名前を変更しても問題ありません：
```bash
python -m ipykernel install --user --name my_custom_kernel --display-name "My Custom Kernel"
```

### 例
```bash
python -m ipykernel install --user --name my_custom_kernel --display-name "My Custom Kernel"
```

これで、Jupyter Notebookのカーネルリストには「My Custom Kernel」と表示されます。

### まとめ
- `--name`オプションはカーネルの内部名を指定し、任意の名前を付けることができます。
- `--display-name`オプションはJupyter Notebookのカーネルリストに表示される名前を指定し、任意の名前を付けることができます。

## カーネルの削除
カーネルの更新のたびに新しい名前を付けると、過去のバージョンのカーネルがパソコンに残ることになります。これにより、不要なカーネルが増えていく可能性があります。

### 不要なカーネルの削除方法
不要なカーネルを削除することで、カーネルのリストを整理することができます。以下のコマンドを使用して、不要なカーネルを削除します。

1. **仮想環境の有効化**:
   まず、仮想環境を有効化します。
   - Windows:
     ```bash
     hogehoge\Scripts\activate
     ```
   - macOS/Linux:
     ```bash
     source hogehoge/bin/activate
     ```

2. **不要なカーネルのリストを表示**:
   インストールされているカーネルのリストを表示します。
   ```bash
   jupyter kernelspec list
   ```

3. **不要なカーネルの削除**:
   不要なカーネルを削除します。例えば、`my_custom_kernel`という名前のカーネルを削除する場合は以下のコマンドを実行します。
   ```bash
   jupyter kernelspec uninstall my_custom_kernel
   ```

### まとめ
- カーネルの更新のたびに名前を変更すると、過去のバージョンのカーネルがパソコンに残ります。
- 不要なカーネルを削除するためには、`jupyter kernelspec uninstall`コマンドを使用します。
