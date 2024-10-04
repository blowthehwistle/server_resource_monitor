# exporters for prometheus

## GPU_exporter
Nvidia GPU exporter by [utkuozdemir](https://github.com/utkuozdemir)

download the latest version from the link below.

https://github.com/utkuozdemir/nvidia_gpu_exporter/releases

check if nvidia-gpu-exporter is in /usr/bin with following command: 
<pre>
<code>dpkg -L nvidia-gpu-exporter</code>
</pre>

the default port is **9835** 


## Node_exporter

Download the latest version from the link below.

https://github.com/prometheus/node_exporter/releases/

<br>

Extract the file using following command:
<pre>
<code>tar xvfz {your file}.tar.gz</code>
</pre>

the default port is **9835** 

To continue collecting metrics, you need to run node_exporter as a background process. To do this, open vi by entering the following command:
<pre>
<code>sudo vi /etc/systemd/system/node_exporter.service</code>
</pre>

Write the following contents to node_exporter.service:
<pre>
<code>[Unit]
Description=Node Exporter
Wants=network-online.target
After=network-online.target

[Service]
User=root
Group=root
Type=simple
ExecStart=/{your}/{node_exporter}/{directory}/{node_exporter}

[Install]
WantedBy=multi-user.target
</code>
</pre>
replace ExecStart with the path where your node_exporter is located.


Now go back and execute the following commands in order:
<pre>
<code>sudo systemctl daemon-reload
sudo systemctl enable node_exporter.service
sudo systemctl start node_exporter.service
</code>
</pre>

