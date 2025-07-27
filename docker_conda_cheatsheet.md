# Docker 和 Conda 命令速查表

## === Docker 容器管理 ===

```bash
drunv   = docker run --rm -it -v <宿主路径>:<容器路径> <镜像> <CMD>        # 挂载当前目录并进入容器
# 示例：docker run --rm -it -v $PWD:/mnt ubuntu bash
dps     = docker ps                         # 列出正在运行的容器
dpsa    = docker ps -a                      # 列出所有容器（包括停止的）
dstop   = docker stop <ID|NAME>             # 停止容器
dstart  = docker start <ID|NAME>            # 启动容器
dexec   = docker exec -it <ID|NAME> bash    # 进入容器新终端
dim     = docker images                     # 列出所有镜像
dpull   = docker pull <REPO:TAG>            # 拉取远程镜像
dcommit = docker commit <容器ID或名称> <新镜像名:tag>  # 将容器保存为新镜像
dpush   = docker push <用户名>/<镜像名>:<tag>         # 上传镜像到 Docker Hub
```

## === 本地镜像使用 ===

```bash
docker run --rm -it -v C:/:/mnt docker.io/antismash/standalone bash       # antiSMASH
docker run --rm -it -v C:/:/mnt docker.io/biopython/biopython bash        # Biopython
docker run --rm -it -v C:/:/mnt docker.io/broadinstitute/gtex_rnaseq bash # GTEx RNA-seq
docker run --rm -it -v C:/:/mnt docker.io/haidyy/run_dbcan bash           # dbCAN
docker run --rm -it -v C:/:/mnt docker.io/ncbi/blast bash                 # NCBI BLAST
docker run --rm -it -v C:/:/mnt docker.io/pyx07/aai-ani-kegg bash         # AAI/ANI/KEGG 综合环境
docker run --rm -it -v C:/:/mnt docker.io/staphb/prokka bash              # Prokka
docker run --rm -it -v C:/:/mnt quay.io/biocontainers/fastspar bash       # FastSpar
docker run --rm -it -v C:/:/mnt quay.io/qiime2/core bash                  # QIIME 2
docker run --rm -it -v C:/:/mnt python bash                               # Python 容器
docker run --rm -it -v C:/:/mnt ubuntu bash                               # Ubuntu 容器
```

## === Conda 安装与配置 ===

```bash
apt update
apt install wget -y
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
chmod +x Miniconda3-latest-*.sh
bash Miniconda3-latest-Linux-x86_64.sh
source ~/miniconda3/bin/activate
conda --version
```

## === 查看安装包版本 ===

```bash
dpkg-query -W -f='${binary:Package}\t${Version}\n'
```

## === Conda 环境与包管理 ===

```bash
cel     = conda env list                      # 查看所有环境
cc      = conda create --name <env>           # 创建新环境
ccy     = conda create --name -y python=3.7   # 创建 Python 3.7 环境
ca      = conda activate <env>                # 激活环境
cde     = conda deactivate                    # 退出环境
cin     = conda install <pkg1> <pkg2>         # 安装包
cup     = conda update <pkg>                  # 更新包
crm     = conda remove <pkg>                  # 删除包
cexp    = conda env export > env.yml          # 导出依赖文件
cimp    = conda env create -f env.yml         # 从依赖文件创建环境
```

## === 常用命令示例 ===

```bash
# 一键运行 UBCG，替换你文件夹的位置
# 示例：C:/Users/DockerVolumes/fasta

docker run --rm -v C:/Users/DockerVolumes/test:/ubcg/uncg/fasta -w /ubcg/uncg pyx07/ubcgv1.3 bash run.sh
```

