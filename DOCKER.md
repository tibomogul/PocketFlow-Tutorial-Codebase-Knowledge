Build the image
```bash
docker build . \
  --build-arg build_docker_uid=$(id -u) \
  --build-arg build_docker_gid=$(id -g) \
  --build-arg build_timezone=Australia/Brisbane \
  -t tibomogul/codebase
```

Set your key
```
export GEMINI_API_KEY=XXXXXXXXXX
```

Exampels on how to run
```bash
docker run --rm -it \
  -v ./vpx/application/angular/:/home/user/code \
  -v ./documentation/vpx_frontend:/home/user/knowledge \
  -e DOCKER_UID=$(id -u) \
  -e DOCKER_GID=$(id -g) \
  -e GEMINI_API_KEY="$GEMINI_API_KEY" \
  tibomogul/codebase \
  bash -lc 'python main.py --dir /home/user/code --output /home/user/knowledge'
```

```bash
docker run --rm -it \
  -v ./lscm-se/httpdocs/:/home/user/code \
  -v ./documentation/lscm-se:/home/user/knowledge \
  -e DOCKER_UID=$(id -u) \
  -e DOCKER_GID=$(id -g) \
  -e GEMINI_API_KEY="$GEMINI_API_KEY" \
  tibomogul/codebase \
  bash -lc 'python main.py --dir /home/user/code --output /home/user/knowledge'
```