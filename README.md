![Logo][logo]
# Workspaces Core Images
This repository contains the base or **"Core"** images from which all other Workspaces images are derived.
These images are based off popular linux distributions and contain the wiring necessary to work within the Kasm platform.

While these images are primarily built to run inside the Kasm platform, they can also be executed manually.  Please note that certain functionality, such as audio, uploads, downloads, and microphone passthrough are only available within the Kasm platform.

```
sudo docker run --rm  -it --shm-size=512m -p 6901:6901 -e VNC_PW=password --build-arg START_XFCE4=1 kasmweb/<image>:<tag>
```

The container is now accessible via a browser : `https://<IP>:6901`

 - **User** : `kasm_user`
 - **Password**: `password`


For more information about building custom images please review the  [**How To Guide**](https://kasmweb.com/docs/latest/how_to/building_images.html?utm_campaign=Github&utm_source=github)

The Kasm team publishes applications and desktop images for use inside the platform. More information, including source can be found in the [Default Images List](https://kasmweb.com/docs/latest/guide/custom_images.html?utm_campaign=Github&utm_source=github)

# About Workspaces
Kasm Workspaces is a docker container streaming platform that enables you to deliver browser-based access to desktops, applications, and web services. Kasm uses a modern DevOps approach for programmatic delivery of services via Containerized Desktop Infrastructure (CDI) technology to create on-demand, disposable, docker containers that are accessible via web browser. The rendering of the graphical-based containers is powered by the open-source project   [**KasmVNC**](https://github.com/kasmtech/KasmVNC?utm_campaign=Github&utm_source=github)

![Screenshot][Kasm_Workflow]

Kasm Workspaces was developed to meet the most demanding secure collaboration requirements that is highly scalable, customizable, and easy to maintain.  Most importantly, Kasm provides a solution, rather than a service, so it is infinitely customizable to your unique requirements and includes a developer API so that it can be integrated with, rather than replace, your existing applications and workflows. Kasm can be deployed in the cloud (Public or Private), on-premise (Including Air-Gapped Networks), or in a hybrid configuration.

# Live Demo
A self-guided on-demand demo is available at [**kasmweb.com**](https://www.kasmweb.com/demo.html?utm_campaign=Github&utm_source=github)


[logo]: https://cdn2.hubspot.net/hubfs/5856039/dockerhub/kasm_logo.png "Kasm Logo"
[Kasm_Workflow]: https://cdn2.hubspot.net/hubfs/5856039/dockerhub/kasm_workflow_960.gif "Kasm Workflow"

sed -i 's/\r$//' filename
sed -i 's/\r$//' src/ubuntu/install/tools/install_tools.sh
sed -i 's/\r$//' src/ubuntu/install/fonts/install_custom_fonts.sh
sed -i 's/\r$//' src/ubuntu/install/xfce/install_xfce_ui.sh
sed -i 's/\r$//' src/ubuntu/install/kasm_vnc/install_kasm_vnc.sh
sed -i 's/\r$//' src/ubuntu/install/kasm_upload_server/install_kasm_upload_server.sh
sed -i 's/\r$//' src/ubuntu/install/audio/install_audio.sh
sed -i 's/\r$//' src/ubuntu/install/audio_input/install_audio_input.sh
sed -i 's/\r$//' src/ubuntu/install/gamepad/install_gamepad.sh
sed -i 's/\r$//' src/ubuntu/install/squid/install/install_squid.sh
sed -i 's/\r$//' src/common/startup_scripts/set_user_permission.sh
sed -i 's/\r$//' src/ubuntu/install/virtualgl/install_virtualgl.sh
sudo docker build -t jimmymax/kasm.root:22.04 -f /audio_input/install_audio_input.shdockerfile-kasm-core .

docker push jimmymax/kasm.root:20.04
sudo docker run --rm  -it --shm-size=512m -p 6901:6901 -e VNC_PW=password --build-arg START_XFCE4=1 jimmymax/kasm.root:20.04
sudo docker run --rm  -it -p 6901:6901 -e VNC_PW=password jimmymax/kasm.root:20.04
docker ps -a | grep "dapr" | awk "{print $3}" | xargs docker rm
