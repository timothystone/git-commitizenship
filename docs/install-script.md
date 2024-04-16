
# Install Script

The following is the install steps followed in the presentation.

##

```shell
npm i -D husky
npx husky init
git config --get core.hookspath
git add --all
git commit --verbose —all
npm i -D @commitlint/cli @commitlint/config-conventional
echo "npx --no -- commitlint --edit \$1" > .husky/commit-msg
chmod +x .husky/commit-msg # optional in Husky v9
cat << EOF > .commitlintrc.js
module.exports = {
  extends: [
    '@commitlint/config-conventional' 
  ],
  rules: {
    'body-empty': [2, 'never'],
    'body-min-length': [2, 'always', 12]
  }
}
EOF
npx commitlint --print-config
git add --all
git commit --verbose —all
npm i -D is-ci
npm pkg set scripts.prepare="is-ci || husky"
```