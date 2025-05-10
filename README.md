<p align="center">
<a href="https://dio.me/"><img src="https://img.shields.io/badge/DIO-Project-FED564?logo=vimeo" alt="DIO - Project"></a>
<a href="https://en.wikipedia.org/wiki/Artificial_intelligence"><img src="https://img.shields.io/badge/AI-Project-FED564?logo=openai" alt="AI - Project"></a>
<a href="https://portal.azure.com/" title="Vá para a página inicial do Portal"><img src="https://custom-icon-badges.demolab.com/badge/Microsoft%20Azure-0089D6?logo=msazure&logoColor=white)](#)"></a>
<a href="https://markdownlivepreview.com/" title="Vá para a página inicial do Editor"><img src="https://img.shields.io/badge/Markdown-%23000000.svg?logo=markdown&logoColor=white"></a>
<a href="https://www.python.org/" title="Vá para a página inicial do Pythonr"><img src="https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=fff"></a>


# Azure Speech Studio e Language Studio

## 🌁 Visão Geral  
Este repositório contém as funcionalidades dos serviços de **análise de fala** e **processamento de linguagem natural** do Azure, com foco em:  
- **Conversão de fala em texto** (Speech-to-Text).  
- **Síntese de voz** (Text-to-Speech).  
- **Reconhecimento de intenções**.  
- **Análise de sentimentos e entidades** (Language Studio).

## 🔧 Ferramentas Utilizadas 🔨


1. **Azure Speech Studio**  
   - Reconhecimento de fala em tempo real.  
   - Customização de modelos acústicos e de linguagem.  
   - Vozes neurais personalizadas.  

2. **Azure Language Studio**  
   - Análise de sentimentos, extração de entidades como pessoas, locais, datas.  
   - Reconhecimento de domínios específicos como jurídico e saúde.  
   - Classificação de texto e detecção de idioma.



## 📝 Anotações e Insights  

### ☑️  Azure Speech Studio  🖲 
- **Speech-to-Text**:  
  - Funciona bem com sotaques e ruídos moderados, mas modelos personalizados melhoram a precisão em cenários específicos (ex: jargões médicos).  
  - Suporta **diarização** (identificação de falantes diferentes).  

- **Text-to-Speech**:  
  - Vozes neurais soam mais naturais que as padrão.  
  - É possível ajustar velocidade, tom e ênfase via Speech Synthesis Markup Language.  

- **Dicas**:  
  - Usar o **Speech SDK** para integrar em aplicações Python e C#.  
  - Testar com áudios curtos antes de processar grandes volumes.  

### ☑️  Azure Language Studio 👅
- **Análise de Sentimentos**:  
  - Classifica textos como positivos, negativos ou neutros e atribui scores de confiança.  
  - Útil para monitoramento de redes sociais ou atendimento ao cliente.  

- **Extração de Entidades**:  
  - Identifica nomes, datas, valores monetários e até relações entre entidades; Exemplo: "João trabalha na Band".  
  - Pode ser combinado com **Reconhecimento de Intenções** para chatbots.  

- **Customização**:  
  - **CLU** (Conversational Language Understanding) facilita a identificação de intenções personalizadas e tornando a configuração mais direta dentro da mesma plataforma do Language Studio. por isso substitui o LUIS para treinar modelos de intenção com exemplos específicos.  

### ⚠️ Desafios Encontrados 🔎
- **Latência** em processamento de áudios longos.  
- **Custos** podem subir rapidamente com alto volume de requisições.  
- **Limitações** em idiomas menos comuns.



### ⏭ Próximos Passos 🚶🏽
1. Integrar os serviços em um **chatbot** usando o Azure Bot Service.  
2. Explorar **personalização avançada** (fine-tuning de modelos para domínios específicos).  
3. Testar **batch processing** para análise de grandes conjuntos de dados.


##  Exemplos de Código  

A seguir, um exemplo simples de como integrar o serviço de transcrição do Azure Speech Studio utilizando Python:

```python
import azure.cognitiveservices.speech as speechsdk

# Configuração da autenticação do serviço
speech_key = "1234567890abcdef1234567890abcdefI"
service_region = "eastus"
speech_config = speechsdk.SpeechConfig(subscription=speech_key, region=service_region)

# Criação do objeto de reconhecedor
audio_config = speechsdk.audio.AudioConfig(filename="Downloads/Azure-Speech/speech.mp3")
speech_recognizer = speechsdk.SpeechRecognizer(speech_config=speech_config, audio_config=audio_config)

# Realiza o reconhecimento
result = speech_recognizer.recognize_once()
if result.reason == speechsdk.ResultReason.RecognizedSpeech:
    print("Transcrição: {}".format(result.text))
else:
    print("Ocorreu um erro durante a transcrição: {}".format(result.reason))
```

## Conclusão

Este projeto me permitiu explorar as funcionalidades do Azure Speech Studio e Language Studio. A conversão de fala em texto e a síntese de voz se mostraram eficazes, com boa precisão e naturalidade. A análise de sentimentos e a extração de entidades foram úteis.

Os próximos passos poderia ser integrar esses serviços em um chatbot e explorar personalizações avançadas fica a sugestão. Essa experiência ampliou meu conhecimento sobre as capacidades do Azure e as aplicações da inteligência artificial.
