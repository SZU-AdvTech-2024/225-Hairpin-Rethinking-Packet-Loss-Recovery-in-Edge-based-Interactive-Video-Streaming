@inproceedings{nsdi2024hairpin,
  title={Hairpin: Rethinking Packet Loss Recovery in Edge-based Interactive Video Streaming},
  author={Meng, Zili and Kong, Xiao and Chen, Jing and Wang, Bo and Xu, Mingwei and Han, Rui and Liu, Honghao and Arun, Venkat and Hu, Hongxin and Wei, Xue},
  booktitle={Proc. USENIX NSDI},
  year={2024}
}

##注意
这里我修改了源代码的rtc-test和Game-Server等相关文件。可以自行对比，只关注与Hairpinone有关的代码即可。

## 安装依赖项
```bash
sudo apt install build-essential libboost-all-dev
```

## 获取最新的 ns-3 源文件
```bash
./setup-env.sh
```

## 构建前进行配置！
对于 ns-3.33 及更低版本，使用 c++14 及以上版本，应按如下方式进行配置：
```bash
LDFLAGS="-lboost_filesystem -lboost_system"./waf configure --cxx-standard=-std=c++17
```

## 复现结果
我们使用 `generate_conf_*` 来生成配置文件，这些文件随后会放入 `*.conf` 文件中。例如，要在 WiFi 跟踪数据中运行 hairpinone 基线，只需运行：
```bash
python run_ns3.py --conf wifi-hairpinone.conf
```
`run_ns3.py` 是一个包装器，用于在不同的跟踪数据上并行运行 ns-3 实验。
