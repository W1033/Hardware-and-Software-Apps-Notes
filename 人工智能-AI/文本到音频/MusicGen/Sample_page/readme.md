# MusicGen: Simple and Controllable Music Generation 

音乐世代：简单可控的音乐生成



> 原文 Original：



## Abstract 抽象

We tackle the task of conditional music generation. We introduce MusicGen, a single Language Model (LM) that operates over several streams of compressed discrete music representation, i.e., tokens. Unlike prior work, MusicGen is comprised of a single-stage transformer LM together with efficient token interleaving patterns, which eliminates the need for cascading several models, e.g., hierarchically or upsampling. Following this approach, we demonstrate how MusicGen can generate high-quality samples, while being conditioned on textual description or melodic features, allowing better controls over the generated output. We conduct extensive empirical evaluation, considering both automatic and human studies, showing the proposed approach is superior to the evaluated baselines on a standard text-to-music benchmark. Through ablation studies, we shed light over the importance of each of the components comprising MusicGen. Music samples can be found on the supplemental materials. Code and models are available on our repo [github.com/facebookresearch/audiocraft](https://github.com/facebookresearch/audiocraft).

我们处理条件音乐生成的任务。我们介绍了MusicGen，这是一种单一语言模型（LM），它可以在多个压缩的离散音乐表示流（即令牌）上运行。与之前的工作不同，MusicGen由单级变压器LM和高效的令牌交错模式组成，无需级联多个模型，例如分层或上采样。遵循这种方法，我们演示了 MusicGen 如何生成高质量的样本，同时以文本描述或旋律特征为条件，从而更好地控制生成的输出。我们进行了广泛的实证评估，考虑了自动和人工研究，表明所提出的方法优于标准文本到音乐基准的评估基线。通过消融研究，我们阐明了构成MusicGen的每个组件的重要性。音乐样本可以在补充材料中找到。代码和模型可在我们的存储库 github.com/facebookresearch/audiocraft 中找到。

Check out our a paper on [Simple and Controllable Music Generation](https://arxiv.org/abs/2306.05284) for more information.
查看我们关于简单可控音乐生成的论文以获取更多信息。

## Samples: comparison to prior work 样本：与先前工作的比较

In the following, we compare MusicGen 3.3B to a number of prior work detailed in the paper: [MusicLM](https://google-research.github.io/seanet/musiclm/examples/), using the public [AI Test Kitchen demo](https://aitestkitchen.withgoogle.com/experiments/music-lm), [Riffusion](https://github.com/riffusion/riffusion) using the provided pre-trained modes, and [Mousai](https://github.com/archinetai/audio-diffusion-pytorch), which we retrained on the same dataset as our proposed MusicGen model.
在下文中，我们将MusicGen 3.3B与论文中详述的一些先前工作进行了比较：MusicLM，使用公共AI测试厨房演示，Riffusion使用提供的预训练模式，以及Mousai，我们在与我们提出的MusicGen模型相同的数据集上重新训练。

| desc 描述                                                    | **MusicGen 音乐世代** | MusicLM 音乐LM | Riffusion 裂缝 | Musai 穆斯泰 |
| ------------------------------------------------------------ | --------------------- | -------------- | -------------- | ------------ |
| Pop dance track with catchy melodies, tropical percussion, and upbeat rhythms, perfect for the beach 流行舞曲，旋律朗朗上口，热带打击乐和欢快的节奏，非常适合海滩 |                       |                |                |              |
| A grand orchestral arrangement with thunderous percussion, epic brass fanfares, and soaring strings, creating a cinematic atmosphere fit for a heroic battle. 宏伟的管弦乐安排，雷鸣般的打击乐，史诗般的铜管乐和高亢的弦乐，营造出适合英勇战斗的电影氛围。 |                       |                |                |              |
| classic reggae track with an electronic guitar solo 经典雷鬼曲目与电子吉他独奏 |                       |                |                |              |
| earthy tones, environmentally conscious, ukulele-infused, harmonic, breezy, easygoing, organic instrumentation, gentle grooves 朴实的色调，环保意识，尤克里里注入，和声，轻快，随和，有机乐器，柔和的凹槽 |                       |                |                |              |
| lofi slow bpm electro chill with organic samples 洛菲慢速BPM电冷却与有机样品 |                       |                |                |              |
| drum and bass beat with intense percussions 鼓和贝斯节拍与强烈的打击乐 |                       |                |                |              |
| A dynamic blend of hip-hop and orchestral elements, with sweeping strings and brass, evoking the vibrant energy of the city. 嘻哈和管弦乐元素的动态融合，宽阔的弦乐和铜管，唤起了这座城市的活力。 |                       |                |                |              |
| violins and synths that inspire awe at the finiteness of life and the universe 小提琴和合成器激发了对生命和宇宙有限性的敬畏 |                       |                |                |              |
| 80s electronic track with melodic synthesizers, catchy beat and groovy bass 80 年代的电子曲目，带有旋律合成器、朗朗上口的节拍和时髦的低音 |                       |                |                |              |
| reggaeton track, with a booming 808 kick, synth melodies layered with Latin percussion elements, uplifting and energizing 雷鬼摇摆乐曲目，轰隆隆的 808 踢，合成器旋律与拉丁打击乐元素分层，令人振奋和充满活力 |                       |                |                |              |
| a piano and cello duet playing a sad chambers music 钢琴和大提琴二重奏演奏悲伤的室内乐 |                       |                |                |              |
| smooth jazz, with a saxophone solo, piano chords, and snare full drums 流畅的爵士乐，萨克斯独奏，钢琴和弦和军鼓 |                       |                |                |              |
| a light and cheerly EDM track, with syncopated drums, aery pads, and strong emotions 轻快的EDM曲目，带有切分鼓，aery打击垫和强烈的情感 |                       |                |                |              |
| a punchy double-bass and a distorted guitar riff 有力的低音提琴和失真的吉他即兴演奏 |                       |                |                |              |
| acoustic folk song to play during roadtrips: guitar flute choirs 公路旅行期间演奏的民歌：吉他长笛合唱团 |                       |                |                |              |
| rock with saturated guitars, a heavy bass line and crazy drum break and fills. 摇滚与饱和的吉他，沉重的低音线和疯狂的鼓破碎和填充。 |                       |                |                |              |

## Melody conditioning 旋律调理

We now experiment with our novel chroma-based melody conditioning. We condition on famous melodies from classical music along with new text description to provide interpretations in any genre or style. We use our MusicGen 1.5B with melody and text conditioning.
我们现在尝试使用基于色度的新型旋律调节。我们以古典音乐中的著名旋律以及新的文本描述为条件，以提供任何流派或风格的解释。我们将MusicGen 1.5B与旋律和文本调节一起使用。

| Source of Melody 旋律来源 | desc 描述                                                    | **MusicGen 音乐世代** |
| ------------------------- | ------------------------------------------------------------ | --------------------- |
|                           | 90s rock song with electric guitar and heavy drums 90年代摇滚歌曲与电吉他和沉重的鼓 |                       |
| -                         | An 80s driving pop song with heavy drums and synth pads in the background 一首 80 年代的流行歌曲，背景是沉重的鼓和合成垫 |                       |
| -                         | An energetic hip-hop music piece, with synth sounds and strong bass. There is a rhythmic hi-hat patten in the drums. 一首充满活力的嘻哈音乐作品，具有合成器声音和强劲的低音。鼓声中有节奏的踩镲。 |                       |
|                           | 90s rock song with electric guitar and heavy drums 90年代摇滚歌曲与电吉他和沉重的鼓 |                       |
| -                         | An 80s driving pop song with heavy drums and synth pads in the background 一首 80 年代的流行歌曲，背景是沉重的鼓和合成垫 |                       |
| -                         | An energetic hip-hop music piece, with synth sounds and strong bass. There is a rhythmic hi-hat patten in the drums. 一首充满活力的嘻哈音乐作品，具有合成器声音和强劲的低音。鼓声中有节奏的踩镲。 |                       |
|                           | 90s rock song with electric guitar and heavy drums 90年代摇滚歌曲与电吉他和沉重的鼓 |                       |
| -                         | An 80s driving pop song with heavy drums and synth pads in the background 一首 80 年代的流行歌曲，背景是沉重的鼓和合成垫 |                       |
| -                         | An energetic hip-hop music piece, with synth sounds and strong bass. There is a rhythmic hi-hat patten in the drums. 一首充满活力的嘻哈音乐作品，具有合成器声音和强劲的低音。鼓声中有节奏的踩镲。 |                       |

## Long generation 长一代

It is possible to generate longer sequence using a fixed 30 seconds windows. We then slide the window by chunks of 10 seconds, keeping the last 20 seconds that were generated as context. We use MusicGen 3.3B.
可以使用固定的 30 秒窗口生成更长的序列。然后，我们将窗口滑动 10 秒的块，将生成的最后 20 秒保留为上下文。我们使用MusicGen 3.3B。

| desc 描述                                                    | **MusicGen 音乐世代** |
| ------------------------------------------------------------ | --------------------- |
| lofi slow bpm electro chill with organic samples 洛菲慢速BPM电冷却与有机样品 |                       |
| a light and cheerly EDM track, with syncopated drums, aery pads, and strong emotions 轻快的EDM曲目，带有切分鼓，aery打击垫和强烈的情感 |                       |
| A grand orchestral arrangement with thunderous percussion, epic brass fanfares, and soaring strings, creating a cinematic atmosphere fit for a heroic battle. 宏伟的管弦乐安排，雷鸣般的打击乐，史诗般的铜管乐和高亢的弦乐，营造出适合英勇战斗的电影氛围。 |                       |