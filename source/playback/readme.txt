playback  ��ϵͳ

רע�� ���� URI(·��) �õ�ԭʼý���ļ���������Ȼ����룬ͨ������󽻸��ط��豸���������ų���

���ϵͳǿ������ֲ�Ժ͸������ԣ�������Ч�ļ���һЩר�ŵ�Ӳ��

��Ҫ������һ��˭���������⣬Ĭ����playback controlģ���������ֲ��ϲ��ţ����ǿ��ǵ�һЩURI�������һЩֱ����Ƶ������Ҳ����һЩ������������ʽ 
������רΪ���ֲ�����ƣ�û��Ҫ��directshowһ������ôǿ�Ŀ���չ�ԣ���

stream  ģ�� 
����һ��URI·���ַ��� �õ�һ��Stream����


�߼�����

m_stream = StreamFactory:CreateStream("http://wwww.xxxx.mp3");
m_decoder = DecoderFactory:CreateDecoderFromStream(m_stream )
m_Outputer = CreateOuptuter()
SoundFormat = Outputer.GetInputFormat()
if m_decoder.supportOutput(soundFormat) then
    self:StartPlayerTimer()
end



function OnTimer
   //��Timer��ȥ�����ݣ�ͬʱ�Ƹ�decoder
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

