# AdaSpeech_Involution
基于CVPR2021Involution改正后的AdaSpeech

语音合成个性化是使用少量数据（几分钟或者几秒钟语音）进行语音定制，现有的方案都是先进行basemodel的训练，然后使用少量数据进行微调​。
现有的个性化面临的​挑战：
1）模型需要支持与训练模型不同的声学条件，因为定制的语音在韵律，音色，环境等等都​不同；
2) 需要支持更多的语音定制，则自适应的​参数应该尽可能的少。为了解决以上的两个问题，
实现采用了了AadSpeech，其主要方式
1）为处理不同的声学条件，添加了句子和音素级别声学模型​。
2）为减少更新的参数量，提出conditional layernorm,只更新speaker embedding和该层​即可。

同时，将原有的conv1d层替换为Involution层，极大的提高了训练和推理速度，实验aishell3中一个说话人选取40句约2.5分钟，在1080ti上训练仅仅花费40分钟即可达到很好的效果（demo文件中包好音频比对）


此代码不包含详细的预处理和训练部分，如有需要请联系cystyle.g@gmail.com


代码参考：
https://github.com/rishikksh20/AdaSpeech2
