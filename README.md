[![Build Status](https://travis-ci.com/Lam0Rka/lab444.svg?branch=main)](https://travis-ci.com/Lam0Rka/lab444)
## Tutorial

```sh
$ export GITHUB_USERNAME=<имя_пользователя>
$ export GITHUB_TOKEN=<полученный_токен>
```

```sh
$ cd ${GITHUB_USERNAME}/workspace
$ pushd .
$ source scripts/activate
```

```sh
$ \curl -sSL https://get.rvm.io | bash -s -- --ignore-dotfiles
$ echo "source $HOME/.rvm/scripts/rvm" >> scripts/activate
$ . scripts/activate
$ rvm autolibs disable
$ rvm install ruby-2.4.2
$ rvm use 2.4.2 --default
$ gem install travis
```

```sh
$ git clone https://github.com/${GITHUB_USERNAME}/lab03 projects/lab04
$ cd projects/lab04
$ git remote remove origin
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab04
```
Установкая языка С++ и дальше в трэвис ямл записываем нужные нам строки
```sh
$ cat > .travis.yml <<EOF
language: cpp
EOF
```

```sh
$ cat >> .travis.yml <<EOF

script:
- cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
- cmake --build _build
- cmake --build _build --target install
EOF
```

```sh
$ cat >> .travis.yml <<EOF

addons:
  apt:
    sources:
      - george-edison55-precise-backports
    packages:
      - cmake
      - cmake-data
EOF
```
логинимся в трэвис
```sh
$ travis login --github-token ${GITHUB_TOKEN}
```

```sh
$ travis lint
```

```sh
$ ex -sc '1i|<фрагмент_вставки_значка>' -cx README.md
```
пушим добавляем
```sh
$ git add .travis.yml
$ git add README.md
$ git commit -m"added CI"
$ git push origin master
```
Показ возможностей трэвиса
```sh
$ travis lint
$ travis accounts
$ travis sync
$ travis repos
$ travis enable
$ travis whatsup
$ travis branches
$ travis history
$ travis show
```
Добавление значков
