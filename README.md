# Mangio-RVC: Retrieval-based Voice Conversion Framework

[![License](https://img.shields.io/github/license/Mangio621/Mangio-RVC-Fork?style=for-the-badge)](LICENSE)
[![Python 3.9](https://img.shields.io/badge/python-3.9-blue.svg?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=for-the-badge&logo=PyTorch&logoColor=white)](https://pytorch.org/)
[![Discord](https://img.shields.io/badge/Discord-7289DA?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/HcsmBBGyVk)

A powerful voice conversion framework based on VITS with top1 retrieval, featuring an easy-to-use WebUI and CLI interface.

## ✨ Features

- **High-Quality Voice Conversion**: Convert voices while preserving singing and speech patterns
- **Multiple F0 Estimation Methods**:
  - Harvest (default)
  - DIO
  - Crepe (full and tiny models)
  - Parselmouth
  - Hybrid mode (combines multiple methods)
- **WebUI & CLI**: Choose your preferred interface
- **Efficient Training**: Works well even with mid-range GPUs
- **Pre-trained Models**: Support for both v1 and v2 model architectures
- **Formant Shifting**: Advanced audio processing capabilities
- **Automatic Audio Processing**: Built-in tools for audio preprocessing

## 🚀 Quick Start

### Prerequisites
- Python 3.9.8
- CUDA-compatible GPU (recommended)
- FFmpeg

### Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/Mangio-RVC.git
cd Mangio-RVC

# Install dependencies
pip install -r requirements.txt

# Download pre-trained models (v2)
python tools/download_models.py --version v2
```

### WebUI

```bash
python infer-web.py
```

### CLI Usage

```bash
# Basic inference
python infer-web.py --is_cli

# Advanced options
python infer-web.py --is_cli --input input.wav --model MyModel.pth --index logs/MyModel/added.index --output output.wav
```

## 📚 Documentation

### Training

1. **Prepare your dataset**
   - Place your audio files in the `dataset/your_model_name/raw` directory
   - Recommended: 10+ minutes of clean speech/singing

2. **Preprocessing**
   ```bash
   python preprocess.py --model_name your_model_name
   ```

3. **Feature Extraction**
   ```bash
   python extract_features.py --model_name your_model_name
   ```

4. **Start Training**
   ```bash
   python train.py --model_name your_model_name --total_epochs 1000
   ```

### Advanced Features

#### Hybrid F0 Estimation
Combine multiple F0 methods for improved results:
```bash
python infer-web.py --is_cli --input input.wav --model MyModel.pth --f0_method hybrid[pm+crepe] --output output.wav
```

#### Formant Shifting
Apply formant shifting during conversion:
```bash
python infer-web.py --is_cli --input input.wav --model MyModel.pth --formant_shift 1.2 --output output.wav
```

## 🤝 Contributing

Contributions are welcome! Please read our [contributing guidelines](CONTRIBUTING.md) before submitting pull requests.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [RVC](https://github.com/RVC-Project/Retrieval-based-Voice-Conversion-WebUI) - The original RVC project
- [VITS](https://github.com/jaywalnut310/vits) - Original VITS implementation
- All contributors and the community

---

💖 Support the project by giving it a star on GitHub!
