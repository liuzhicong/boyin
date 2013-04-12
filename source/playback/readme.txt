playback  子系统

专注于 根据 URI(路径) 得到原始媒体文件数据流，然后解码，通过处理后交给回放设备把声音播放出来

这个系统强调可移植性和高性能性，并能有效的集成一些专门的硬件

主要这里有一个谁驱动的问题，默认由playback control模块驱动音乐不断播放，但是考虑到一些URI代表的是一些直播音频，所以也允许一些其它的驱动方式 
（由于专为音乐播放设计，没必要像directshow一样有那么强的可扩展性？）

stream  模块 
根据一个URI路径字符串 得到一个Stream对象


逻辑代码

m_stream = StreamFactory:CreateStream("http://wwww.xxxx.mp3");
m_decoder = DecoderFactory:CreateDecoderFromStream(m_stream )
m_Outputer = CreateOuptuter()
SoundFormat = Outputer.GetInputFormat()
if m_decoder.supportOutput(soundFormat) then
    self:StartPlayerTimer()
end



function OnTimer
   //在Timer中去拿数据，同时推给decoder
   data = GetRawDataFromCache()
   if m_cache.needEecoder then
      filedata = m_stream.read()
      filedata = m_decoder.push(data,onDecoderSuccess)
   end

   if m_eq then
      m_eq.process(rawdata)
   end

   m_outputer.playback(rawdata)
end



end

