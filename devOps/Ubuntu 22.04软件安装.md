# Python

- 系统默认预先安装了Python 3.10.12
- 自定义安装版本

## Deadsnakes PPA安装

- 最后的小版本，如果开发环境和部署环境不同，没什么大的问题

```bash
# 添加 PPA 源
sudo add-apt-repository ppa:deadsnakes/ppa -y
sudo apt update

# 安装指定版本（以 3.13 为例）
# 查看候选版本
apt policy python3.13    

python3.13:
  Installed: (none)
  Candidate: 3.13.14-1+jammy1  (即将安装的版本)
  Version table:
     3.13.14-1+jammy1 500
        500 https://ppa.launchpadcontent.net/deadsnakes/ppa/ubuntu jammy/main amd64 Packages

# 安装
sudo apt install python3.13 python3.13-venv python3.13-dev -y

# 验证
python3.13 --version
# 输出: Python 3.13.x
```

