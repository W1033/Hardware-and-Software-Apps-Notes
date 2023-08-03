# MusicGen: Simple and Controllable Music Generation 

音乐世代：简单可控的音乐生成



> https://github.com/facebookresearch/audiocraft/blob/main/docs/MUSICGEN.md





AudioCraft provides the code and models for MusicGen, [a simple and controllable model for music generation](https://arxiv.org/abs/2306.05284). MusicGen is a single stage auto-regressive Transformer model trained over a 32kHz [EnCodec tokenizer](https://github.com/facebookresearch/encodec) with 4 codebooks sampled at 50 Hz. Unlike existing methods like [MusicLM](https://arxiv.org/abs/2301.11325), MusicGen doesn't require a self-supervised semantic representation, and it generates all 4 codebooks in one pass. By introducing a small delay between the codebooks, we show we can predict them in parallel, thus having only 50 auto-regressive steps per second of audio. Check out our [sample page](https://ai.honu.io/papers/musicgen/) or test the available demo!
AudioCraft 为 MusicGen 提供了代码和模型，这是一个简单且可控的音乐生成模型。MusicGen 是一种单级自回归变压器模型，通过 32kHz EnCodec 分词器进行训练，其中 4 本码本以 50 Hz 采样。与 MusicLM 等现有方法不同，MusicGen 不需要自我监督的语义表示，它可以一次性生成所有 4 个密码本。通过在码本之间引入一个小的延迟，我们展示了我们可以并行预测它们，因此每秒只有 50 个自回归步长的音频。查看我们的示例页面或测试可用的演示！

Open In Colab、Open in HugginFace

We use 20K hours of licensed music to train MusicGen. Specifically, we rely on an internal dataset of 10K high-quality music tracks, and on the ShutterStock and Pond5 music data.
我们使用20K小时的授权音乐来训练MusicGen。具体来说，我们依赖于10K高质量音乐曲目的内部数据集，以及ShutterStock和Pond5音乐数据。

## Model Card 模型卡

See [the model card](https://github.com/facebookresearch/audiocraft/blob/main/model_cards/MUSICGEN_MODEL_CARD.md). 请参阅模型卡。

## Installation 安装

Please follow the AudioCraft installation instructions from the [README](https://github.com/facebookresearch/audiocraft/blob/main/README.md).
请按照自述文件中的音频工艺安装说明进行操作。

AudioCraft requires a GPU with at least 16 GB of memory for running inference with the medium-sized models (~1.5B parameters).
AudioCraft 需要至少具有 16 GB 内存的 GPU 才能使用中型模型（~1.5B 参数）运行推理。

## Usage 用法

We offer a number of way to interact with MusicGen:
我们提供多种与MusicGen互动的方式：

1. A demo is also available on the [`facebook/MusicGen` Hugging Face Space](https://huggingface.co/spaces/facebook/MusicGen) (huge thanks to all the HF team for their support).
    `facebook/MusicGen` Hugging Face Space上也提供了一个演示（非常感谢所有HF团队的支持）。
2. You can run the extended demo on a Colab: [colab notebook](https://colab.research.google.com/drive/1JlTOjB-G0A2Hz3h8PK63vLZk4xdCI5QB?usp=sharing)
    您可以在 Colab 上运行扩展演示：colab 笔记本
3. You can use the gradio demo locally by running [`python -m demos.musicgen_app --share`](https://github.com/facebookresearch/audiocraft/blob/main/demos/musicgen_app.py).
    您可以通过运行 `python -m demos.musicgen_app --share` 在本地使用 gradio 演示。
4. You can play with MusicGen by running the jupyter notebook at [`demos/musicgen_demo.ipynb`](https://github.com/facebookresearch/audiocraft/blob/main/demos/musicgen_demo.ipynb) locally (if you have a GPU).
    您可以通过 `demos/musicgen_demo.ipynb` 在本地运行 jupyter 笔记本来玩 MusicGen（如果您有 GPU）。
5. Finally, checkout [@camenduru Colab page](https://github.com/camenduru/MusicGen-colab) which is regularly updated with contributions from @camenduru and the community.
    最后，结帐@camenduru Colab页面，该页面会定期更新@camenduru和社区的贡献。

## API 应用程序接口

We provide a simple API and 4 pre-trained models. The pre trained models are:
我们提供一个简单的 API 和 4 个预训练模型。预训练的模型是：

- `facebook/musicgen-small`: 300M model, text to music only - [Hub](https://huggingface.co/facebook/musicgen-small)
    `facebook/musicgen-small` ：300M型号，仅文本到音乐 - 集线器
- `facebook/musicgen-medium`: 1.5B model, text to music only - [Hub](https://huggingface.co/facebook/musicgen-medium)
    `facebook/musicgen-medium` ：1.5B 型号，仅文本到音乐 - 集线器
- `facebook/musicgen-melody`: 1.5B model, text to music and text+melody to music - [Hub](https://huggingface.co/facebook/musicgen-melody)
    `facebook/musicgen-melody` ：1.5B型号，文本到音乐和文本+旋律到音乐 - 集线器
- `facebook/musicgen-large`: 3.3B model, text to music only - [Hub](https://huggingface.co/facebook/musicgen-large)
    `facebook/musicgen-large` ：3.3B型号，仅文本到音乐 - 集线器

We observe the best trade-off between quality and compute with the `facebook/musicgen-medium` or `facebook/musicgen-melody` model. In order to use MusicGen locally **you must have a GPU**. We recommend 16GB of memory, but smaller GPUs will be able to generate short sequences, or longer sequences with the `facebook/musicgen-small` model.
我们观察到 `facebook/musicgen-medium` or `facebook/musicgen-melody` 模型在质量和计算之间的最佳权衡。为了在本地使用MusicGen，您必须有一个GPU。我们建议使用 16GB 内存，但较小的 GPU 将能够使用 `facebook/musicgen-small` 模型生成短序列或较长的序列。

See after a quick example for using the API.
请参阅有关使用 API 的快速示例。

```
import torchaudio
from audiocraft.models import MusicGen
from audiocraft.data.audio import audio_write

model = MusicGen.get_pretrained('facebook/musicgen-melody')
model.set_generation_params(duration=8)  # generate 8 seconds.
wav = model.generate_unconditional(4)    # generates 4 unconditional audio samples
descriptions = ['happy rock', 'energetic EDM', 'sad jazz']
wav = model.generate(descriptions)  # generates 3 samples.

melody, sr = torchaudio.load('./assets/bach.mp3')
# generates using the melody from the given audio and the provided descriptions.
wav = model.generate_with_chroma(descriptions, melody[None].expand(3, -1, -1), sr)

for idx, one_wav in enumerate(wav):
    # Will save under {idx}.wav, with loudness normalization at -14 db LUFS.
    audio_write(f'{idx}', one_wav.cpu(), model.sample_rate, strategy="loudness", loudness_compressor=True)
```



## Transformers Usage 变压器的使用

MusicGen is available in the Transformers library from version 4.31.0 onwards, requiring minimal dependencies and additional packages. Steps to get started:
从版本 4.31.0 开始，MusicGen 在变形金刚库中可用， 需要最少的依赖项和额外的包。入门步骤：

1. First install the [Transformers library](https://github.com/huggingface/transformers) from main:
    首先从 主安装变压器库：

```
pip install git+https://github.com/huggingface/transformers.git
```



1. Run the following Python code to generate text-conditional audio samples:
    运行以下 Python 代码以生成文本条件音频示例：

```
from transformers import AutoProcessor, MusicgenForConditionalGeneration


processor = AutoProcessor.from_pretrained("facebook/musicgen-small")
model = MusicgenForConditionalGeneration.from_pretrained("facebook/musicgen-small")

inputs = processor(
    text=["80s pop track with bassy drums and synth", "90s rock song with loud guitars and heavy drums"],
    padding=True,
    return_tensors="pt",
)

audio_values = model.generate(**inputs, max_new_tokens=256)
```



1. Listen to the audio samples either in an ipynb notebook:
    在ipynb笔记本中收听音频样本：

```
from IPython.display import Audio

sampling_rate = model.config.audio_encoder.sampling_rate
Audio(audio_values[0].numpy(), rate=sampling_rate)
```



Or save them as a `.wav` file using a third-party library, e.g. `scipy`:
或者使用第三方库将它们另存为 `.wav` 文件，例如 `scipy` ：

```
import scipy

sampling_rate = model.config.audio_encoder.sampling_rate
scipy.io.wavfile.write("musicgen_out.wav", rate=sampling_rate, data=audio_values[0, 0].numpy())
```



For more details on using the MusicGen model for inference using the Transformers library, refer to the [MusicGen docs](https://huggingface.co/docs/transformers/main/en/model_doc/musicgen) or the hands-on [Google Colab](https://colab.research.google.com/github/sanchit-gandhi/notebooks/blob/main/MusicGen.ipynb).
有关使用 MusicGen 模型通过变形金刚库进行 推理的更多详细信息，请参阅 MusicGen 文档或动手操作的 Google Colab。

## Training 训练

The [MusicGenSolver](https://github.com/facebookresearch/audiocraft/blob/main/audiocraft/solvers/musicgen.py) implements MusicGen's training pipeline. It defines an autoregressive language modeling task over multiple streams of discrete tokens extracted from a pre-trained EnCodec model (see [EnCodec documentation](https://github.com/facebookresearch/audiocraft/blob/main/docs/ENCODEC.md) for more details on how to train such model).
MusicGenSolver实现了MusicGen的训练管道。它针对从预训练的 EnCodec 模型中提取的多个离散标记流定义自回归语言建模任务（有关如何训练此类模型的更多详细信息，请参阅 EnCodec 文档）。

Note that **we do NOT provide any of the datasets** used for training MusicGen. We provide a dummy dataset containing just a few examples for illustrative purposes.
请注意，我们不提供任何用于训练MusicGen的数据集。我们提供了一个虚拟数据集，仅包含几个示例，用于说明目的。

Please read first the [TRAINING documentation](https://github.com/facebookresearch/audiocraft/blob/main/docs/TRAINING.md), in particular the Environment Setup section.
请首先阅读培训文档，特别是环境设置部分。

### Example configurations and grids 示例配置和网格

We provide configurations to reproduce the released models and our research. MusicGen solvers configuration are available in [config/solver/musicgen](https://github.com/facebookresearch/audiocraft/blob/main/config/solver/musicgen), in particular:
我们提供配置来重现已发布的模型和我们的研究。MusicGen 求解器配置在 config/solver/musicgen 中可用，特别是：

- MusicGen base model for text-to-music: [`solver=musicgen/musicgen_base_32khz`](https://github.com/facebookresearch/audiocraft/blob/main/config/solver/musicgen/musicgen_base_32khz.yaml)
    文本到音乐的音乐生成基本模型： `solver=musicgen/musicgen_base_32khz`
- MusicGen model with chromagram-conditioning support: [`solver=musicgen/musicgen_melody_32khz`](https://github.com/facebookresearch/audiocraft/blob/main/config/solver/musicgen/musicgen_melody_32khz.yaml)
    支持色谱图调节的 MusicGen 模型： `solver=musicgen/musicgen_melody_32khz`

We provide 3 different scales, e.g. `model/lm/model_scale=small` (300M), or `medium` (1.5B), and `large` (3.3B).
我们提供 3 种不同的刻度，例如 （300M）、或 `model/lm/model_scale=small` `medium` （1.5B） 和 `large` （3.3B）。

Please find some example grids to train MusicGen at [audiocraft/grids/musicgen](https://github.com/facebookresearch/audiocraft/blob/main/audiocraft/grids/musicgen).
请在audiocraft/grids/musicgen找到一些训练MusicGen的示例网格。

```
# text-to-music
dora grid musicgen.musicgen_base_32khz --dry_run --init
# melody-guided music generation
dora grid musicgen.musicgen_melody_base_32khz --dry_run --init
# Remove the `--dry_run --init` flags to actually schedule the jobs once everything is setup.
```



### Music dataset and metadata 音乐数据集和元数据

MusicGen's underlying dataset is an AudioDataset augmented with music-specific metadata. The MusicGen dataset implementation expects the metadata to be available as `.json` files at the same location as the audio files. Learn more in the [datasets section](https://github.com/facebookresearch/audiocraft/blob/main/docs/DATASETS.md).
MusicGen的基础数据集是一个使用特定于音乐的元数据增强的AudioDataset。MusicGen 数据集实现希望元数据作为文件在 `.json` 与音频文件相同的位置提供。有关详细信息，请参阅数据集部分。

### Audio tokenizers 音频标记器

We support a number of audio tokenizers: either pretrained EnCodec models, [DAC](https://github.com/descriptinc/descript-audio-codec), or your own models. The tokenizer is controlled with the setting `compression_model_checkpoint`. For instance,
我们支持多种音频分词器：预训练的 EnCodec 模型、DAC 或您自己的模型。分词器由设置 `compression_model_checkpoint` .例如

```
# Using the 32kHz EnCodec trained on music
dora run solver=musicgen/debug \
    compression_model_checkpoint=//pretrained/facebook/encodec_32khz \
    transformer_lm.n_q=4 transformer_lm.card=2048

# Using DAC
dora run solver=musicgen/debug \
    compression_model_checkpoint=//pretrained/dac_44khz \
    transformer_lm.n_q=9 transformer_lm.card=1024 \
    'codebooks_pattern.delay.delays=[0,1,2,3,4,5,6,7,8]'

# Using your own model after export (see ENCODEC.md)
dora run solver=musicgen/debug \
    compression_model_checkpoint=//pretrained//checkpoints/my_audio_lm/compression_state_dict.bin \
    transformer_lm.n_q=... transformer_lm.card=...

# Using your own model from its training checkpoint.
dora run solver=musicgen/debug \
    compression_model_checkpoint=//sig/SIG \ # where SIG is the Dora signature of the EnCodec XP.
    transformer_lm.n_q=... transformer_lm.card=...
```



**Warning:** you are responsible for setting the proper value for `transformer_lm.n_q` and `transformer_lm.card` (cardinality of the codebooks). You also have to update the codebook_pattern to match `n_q` as shown in the example for using DAC. .
警告：您负责为 `transformer_lm.n_q` 和 `transformer_lm.card` （码本的基数）设置正确的值。您还必须更新codebook_pattern以匹配 `n_q` ，如使用 DAC 的示例所示。.

### Fine tuning existing models 微调现有模型

You can initialize your model to one of the pretrained models by using the `continue_from` argument, in particular
您可以使用参数 `continue_from` 将模型初始化为其中一个预训练模型，特别是

```
# Using pretrained MusicGen model.
dora run solver=musicgen/musicgen_base_32khz model/lm/model_scale=medium continue_from=//pretrained/facebook/musicgen-medium conditioner=text2music

# Using another model you already trained with a Dora signature SIG.
dora run solver=musicgen/musicgen_base_32khz model/lm/model_scale=medium continue_from=//sig/SIG conditioner=text2music

# Or providing manually a path
dora run solver=musicgen/musicgen_base_32khz model/lm/model_scale=medium continue_from=/checkpoints/my_other_xp/checkpoint.th
```



**Warning:** You are responsible for selecting the other parameters accordingly, in a way that make it compatible with the model you are fine tuning. Configuration is NOT automatically inherited from the model you continue from. In particular make sure to select the proper `conditioner` and `model/lm/model_scale`.
警告：您有责任相应地选择其他参数，使其与您正在微调的模型兼容。配置不会自动继承自您继续使用的模型。特别是确保选择正确的 `conditioner` 和 `model/lm/model_scale` .

**Warning:** We currently do not support fine tuning a model with slightly different layers. If you decide to change some parts, like the conditioning or some other parts of the model, you are responsible for manually crafting a checkpoint file from which we can safely run `load_state_dict`. If you decide to do so, make sure your checkpoint is saved with `torch.save` and contains a dict `{'best_state': {'model': model_state_dict_here}}`. Directly give the path to `continue_from` without a `//pretrained/` prefix.
警告：我们目前不支持微调层略有不同的模型。如果您决定更改某些部分，例如条件反射或模型的其他一些部分，则需负责手动制作一个检查点文件，我们可以从中安全运行 `load_state_dict` 。如果您决定这样做，请确保您的检查点与 一起 `torch.save` 保存并包含字典 `{'best_state': {'model': model_state_dict_here}}` 。直接给出不 `continue_from` 带 `//pretrained/` 前缀的路径。

### Caching of EnCodec tokens 编码令牌的缓存

It is possible to precompute the EnCodec tokens and other metadata. An example of generating and using this cache provided in the [musicgen.musicgen_base_cached_32khz grid](https://github.com/facebookresearch/audiocraft/blob/main/audiocraft/grids/musicgen/musicgen_base_cached_32khz.py).
可以预先计算编码令牌和其他元数据。生成和使用此缓存的示例musicgen.musicgen_base_cached_32khz网格中提供。

### Evaluation stage 评估阶段

By default, evaluation stage is also computing the cross-entropy and the perplexity over the evaluation dataset. Indeed the objective metrics used for evaluation can be costly to run or require some extra dependencies. Please refer to the [metrics documentation](https://github.com/facebookresearch/audiocraft/blob/main/docs/METRICS.md) for more details on the requirements for each metric.
默认情况下，评估阶段也在计算评估数据集上的交叉熵和困惑度。事实上，用于评估的客观指标的运行成本可能很高，或者需要一些额外的依赖关系。有关每个指标要求的更多详细信息，请参阅指标文档。

We provide an off-the-shelf configuration to enable running the objective metrics for audio generation in [config/solver/musicgen/evaluation/objective_eval](https://github.com/facebookresearch/audiocraft/blob/main/config/solver/musicgen/evaluation/objective_eval.yaml).
我们提供了一个现成的配置，以便在配置/求解器/音乐生成/评估/objective_eval中运行音频生成的客观指标。

One can then activate evaluation the following way:
然后可以通过以下方式激活评估：

```
# using the configuration
dora run solver=musicgen/debug solver/musicgen/evaluation=objective_eval
# specifying each of the fields, e.g. to activate KL computation
dora run solver=musicgen/debug evaluate.metrics.kld=true
```



See [an example evaluation grid](https://github.com/facebookresearch/audiocraft/blob/main/audiocraft/grids/musicgen/musicgen_pretrained_32khz_eval.py).
请参阅示例评估网格。

### Generation stage 生成阶段

The generation stage allows to generate samples conditionally and/or unconditionally and to perform audio continuation (from a prompt). We currently support greedy sampling (argmax), sampling from softmax with a given temperature, top-K and top-P (nucleus) sampling. The number of samples generated and the batch size used are controlled by the `dataset.generate` configuration while the other generation parameters are defined in `generate.lm`.
生成阶段允许有条件和/或无条件地生成样本，并执行音频延续（从提示）。我们目前支持贪婪采样（argmax），从给定温度的softmax采样，top-K和top-P（细胞核）采样。生成的样本数和使用的批大小由 `dataset.generate` 配置控制，而其他生成参数在 中 `generate.lm` 定义。

```
# control sampling parameters
dora run solver=musicgen/debug generate.lm.gen_duration=10 generate.lm.use_sampling=true generate.lm.top_k=15
```



#### Listening to samples 聆听样本

Note that generation happens automatically every 25 epochs. You can easily access and compare samples between models (as long as they are trained) on the same dataset using the MOS tool. For that first `pip install Flask gunicorn`. Then
请注意，每 25 个纪元自动生成一次。您可以使用 MOS 工具轻松访问和比较同一数据集上模型之间的样本（只要它们经过训练）。对于第一个 `pip install Flask gunicorn` .然后

```
gunicorn -w 4 -b 127.0.0.1:8895 -t 120 'scripts.mos:app'  --access-logfile -
```



And access the tool at [https://127.0.0.1:8895](https://127.0.0.1:8895/).
并在 https://127.0.0.1:8895 访问该工具。

### Playing with the model 玩转模型

Once you have launched some experiments, you can easily get access to the Solver with the latest trained model using the following snippet.
启动一些试验后，可以使用以下代码片段轻松访问具有最新训练模型的规划求解。

```
from audiocraft.solvers.musicgen import MusicGen

solver = MusicGen.get_eval_solver_from_sig('SIG', device='cpu', batch_size=8)
solver.model
solver.dataloaders
```



### Importing / Exporting models 导入/导出模型

We do not support currently loading a model from the Hugging Face implementation or exporting to it. If you want to export your model in a way that is compatible with `audiocraft.models.MusicGen` API, you can run:
我们当前不支持从拥抱脸实现加载模型或导出到该模型。如果要以与 `audiocraft.models.MusicGen` API 兼容的方式导出模型，可以运行：

```
from audiocraft.utils import export
from audiocraft import train
xp = train.main.get_xp_from_sig('SIG_OF_LM')
export.export_lm(xp.folder / 'checkpoint.th', '/checkpoints/my_audio_lm/state_dict.bin')
# You also need to bundle the EnCodec model you used !!
## Case 1) you trained your own
xp_encodec = train.main.get_xp_from_sig('SIG_OF_ENCODEC')
export.export_encodec(xp_encodec.folder / 'checkpoint.th', '/checkpoints/my_audio_lm/compression_state_dict.bin')
## Case 2) you used a pretrained model. Give the name you used without the //pretrained/ prefix.
## This will actually not dump the actual model, simply a pointer to the right model to download.
export.export_pretrained_compression_model('facebook/encodec_32khz', '/checkpoints/my_audio_lm/compression_state_dict.bin')
```



Now you can load your custom model with:
现在，您可以使用以下内容加载自定义模型：

```
import audiocraft.models
musicgen = audiocraft.models.MusicGen.get_pretrained('/checkpoints/my_audio_lm/')
```



### Learn more 了解更多信息

Learn more about AudioCraft training pipelines in the [dedicated section](https://github.com/facebookresearch/audiocraft/blob/main/docs/TRAINING.md).
在专用部分中了解有关 AudioCraft 培训管道的更多信息。

## FAQ 常见问题

#### I need help on Windows 我需要有关 Windows 的帮助

@FurkanGozukara made a complete tutorial for [AudioCraft/MusicGen on Windows](https://youtu.be/v-YpvPkhdO4)
@FurkanGozukara为Windows上的AudioCraft/MusicGen制作了一个完整的教程

#### I need help for running the demo on Colab 我需要帮助在 Colab 上运行演示

Check [@camenduru tutorial on YouTube](https://www.youtube.com/watch?v=EGfxuTy9Eeo).
查看YouTube上的@camenduru教程。

#### What are top-k, top-p, temperature and classifier-free guidance? 什么是无顶k、顶p、温度和无分类器指导？

Check out [@FurkanGozukara tutorial](https://github.com/FurkanGozukara/Stable-Diffusion/blob/main/Tutorials/AI-Music-Generation-Audiocraft-Tutorial.md#more-info-about-top-k-top-p-temperature-and-classifier-free-guidance-from-chatgpt).
查看@FurkanGozukara教程。

#### Should I use FSDP or autocast ? 我应该使用 FSDP 还是自动广播？

The two are mutually exclusive (because FSDP does autocast on its own). You can use autocast up to 1.5B (medium), if you have enough RAM on your GPU. FSDP makes everything more complex but will free up some memory for the actual activations by sharding the optimizer state.
这两者是相互排斥的（因为FSDP本身会自动广播）。如果您的 GPU 上有足够的 RAM，您可以使用高达 1.5B（中等）的自动广播。FSDP 使一切变得更加复杂，但会通过对优化器状态进行分片，为实际激活释放一些内存。

## Citation 报价单

```
@article{copet2023simple,
    title={Simple and Controllable Music Generation},
    author={Jade Copet and Felix Kreuk and Itai Gat and Tal Remez and David Kant and Gabriel Synnaeve and Yossi Adi and Alexandre Défossez},
    year={2023},
    journal={arXiv preprint arXiv:2306.05284},
}
```



## License 许可证

See license information in the [model card](https://github.com/facebookresearch/audiocraft/blob/main/model_cards/MUSICGEN_MODEL_CARD.md).
请参阅模型卡中的许可证信息。