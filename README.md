# Portfolio
This portofolio is a collaborative archive of IT with graphic visual art, showing inner self-expression as well as displaying video works I have created so far.

# 1. 進行中の同期を止めた後、リモートの状態までコミットを安全に戻す（変更は残る）
git reset --soft origin/main

# 2. 全てのステージングを解除する
git reset

# 3. .gitignore に重いファイル（例: *.mp4）を追記後、不要なGitキャッシュを掃除する
git gc --prune=now

# 4. コードなどの軽量ファイルのみを追加して再コミット＆送信
git add .
git commit -m "clean commit"
git push origin main

# コミット対象に含まれる巨大ファイル TOP10 を表示
git ls-files -s | sort -k4 -n -r | head -n 10

# 現在の変更・ステージング状態の確認
git status

# 過去の操作履歴・コミット履歴（reflog）の確認
git reflog

# 手元の変更を残したまま直前 1 件のコミットを取り消す
git reset --soft HEAD~1

# 手元の変更を残したままリモート（origin/main）の状態まで取り消す
git reset --soft origin/main

# 特定コミットまたは reflog の位置へ強制復元（※未コミットの変更は消えるため注意）
git reset --hard <コミットIDまたはHEAD@{n}>

# 単一のファイルを Git 管理対象から外す
git rm --cached "path/to/file.mp4"

# フォルダ全体を Git 管理対象から外す
git rm --cached -r "path/to/folder/"

# 特定の拡張子を一括でステージング解除
git restore --staged *.mp4

# Media
*.mp4
*.mov
*.avi
*.zip

# Dependencies & Builds
node_modules/
dist/
build/