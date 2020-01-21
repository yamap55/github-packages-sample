# github-package-registry-sample

## docker
### 格納手順
1. トークンの作成
    - https://github.com/settings/tokens/new
    - 許可 : repo, write:packages, read:packages, delete:packages
    - [参考ページ](https://help.github.com/ja/github/managing-packages-with-github-packages/about-github-packages#about-tokens)
2. docker login
    - `docker login docker.pkg.github.com -u USERNAME -p TOKEN`
    - 例 : `docker login docker.pkg.github.com -u yamap55 -p 8982f91d09e95dda471d67ff9f68408eed9adc8c`
3. docker build
    - `docker build -t docker.pkg.github.com/OWNER/REPOSITORY/IMAGE_NAME:VERSION PATH`
    - 例 : `docker build -t docker.pkg.github.com/yamap55/github-package-registry-sample/sample-img:1.0 .`
4. docker push
    - `docker push docker.pkg.github.com/OWNER/REPOSITORY/IMAGE_NAME:VERSION`
    - 例 : `docker push docker.pkg.github.com/yamap55/github-package-registry-sample/sample-img:1.0`
5. 確認
    - https://github.com/USER_NAME/REPOSITORY_NAME/packages
    - 例 : https://github.com/yamap55/github-package-registry-sample/packages
    - たまに、ある程度の時間がたたないとリポジトリのタブにpackageは表示されない事があります

### 使用する
- docker pull
    - `docker pull docker.pkg.github.com/yamap55/github-package-registry-sample/sample-img:1.0`
- dockerfile
    - `FROM docker.pkg.github.com/yamap55/github-package-registry-sample/sample-img:1.0`
