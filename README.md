せっかくだから仮想環境の勉強もついででやっています。  
早速自分のPCのカーネル作成ミスった説出てきました。  
思ったけどJupyternotebook動かしてるライブラリの環境とかをローカルに移したい時ってどういう事すればええんかな  

- 現在インストールしたライブラリ
  - matplot  
  - ipykernel

- カーネルのコマンド
```
python -m ipykernel install --user --name newenv --display-name "Jupyter_Sample"
```
