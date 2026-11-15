# Política de Privacidade — Electric Eye (SpectrumMonitor)

**Última atualização:** 15 de novembro de 2026  
**Desenvolvedor responsável:** Fabrício Vieira Sanfelice  
**Marca:** TradeVSan  
**Contato:** suportetradevsan@gmail.com

Esta Política de Privacidade explica como o aplicativo **Electric Eye (SpectrumMonitor)** trata permissões, sensores e dados no seu dispositivo Android.

---

## 1. Resumo de Privacidade

O **Electric Eye** processa as leituras dos sensores físicos localmente no seu aparelho (*on-device*). **Não operamos servidores próprios de coleta**, não vendemos dados pessoais e não utilizamos redes de anúncios ou rastreadores comportamentais de terceiros.

---

## 2. Permissões e Dados Tratados no Dispositivo

As permissões solicitadas pelo aplicativo destinam-se exclusivamente ao funcionamento técnico dos instrumentos de leitura:

- **Câmera (`CAMERA`):** Utilizada apenas no modo **Visão AR (Realidade Aumentada)** para exibir a visualização da câmera em tempo real com camadas espectrais sobrepostas. O fluxo de vídeo não é enviado a servidores externos; capturas de tela ou imagens geradas só são compartilhadas quando você aciona o compartilhamento manualmente.
- **Microfone (`RECORD_AUDIO`):** Utilizado para calcular pressão sonora (decibéis) e análise espectral acústica (FFT) em tempo real na memória do aparelho. O áudio **não é gravado em arquivo** nem transmitido pela internet.
- **Localização (`ACCESS_FINE_LOCATION` e `ACCESS_COARSE_LOCATION`):**
  - Exigida pelo sistema Android para leitura local de informações de Wi-Fi/RF.
  - Por padrão, **o envio de localização para serviços externos fica desativado**, utilizando coordenadas fixas de referência (São Paulo, SP).
  - Caso você ative manualmente a opção **"Privacidade da Consulta Solar & Geiger"**, o aplicativo envia apenas coordenadas **arredondadas para 2 casas decimais** (precisão aproximada de bairro/cidade) para consultar dados ambientais públicos.
  - Coordenadas locais recentes podem ser registradas no histórico de alertas armazenado no próprio dispositivo (`hazard_incidents.json`) quando um evento físico relevante é detectado, além de poderem ser abertas em aplicativos de mapas externos apenas quando você tocar nessa ação.
- **Wi-Fi e Bluetooth (`ACCESS_WIFI_STATE`, `CHANGE_WIFI_STATE`, `NEARBY_WIFI_DEVICES`, `BLUETOOTH`, `BLUETOOTH_ADMIN`, `BLUETOOTH_SCAN`):** Utilizados localmente para estimar a intensidade de sinais de radiofrequência próximos. As permissões modernas de varredura utilizam a declaração `neverForLocation`.

---

## 3. Serviços Externos e Compartilhamento de Dados

Quando o dispositivo possui acesso à internet (`INTERNET` e `ACCESS_NETWORK_STATE`), o aplicativo realiza consultas exclusivamente aos seguintes serviços:

1. **Open-Meteo (`api.open-meteo.com` e `air-quality-api.open-meteo.com`):** Fornece dados públicos de índice UV, irradiância solar e qualidade do ar/ozônio. Recebe apenas coordenadas fixas de referência ou coordenadas aproximadas (2 casas decimais, se autorizado por você), além dos metadados padrão de rede (como endereço IP) inerentes a conexões HTTPS.
2. **Safecast (`api.safecast.org`):** Fornece medições públicas da rede cidadã de contadores Geiger próximos, utilizando as mesmas regras de localização padrão ou aproximada descritas acima.
3. **NOAA SWPC (`services.swpc.noaa.gov`):** Fornece telemetria espacial pública (raios X solares, índice geomagnético Kp e vento solar), sem envio de localização ou identificação do usuário.
4. **Google Gemini API (`generativelanguage.googleapis.com`):** Acionada **somente quando você solicita explicitamente** uma auditoria técnica ou envia uma pergunta no Consultor IA. Nessa solicitação, são enviados o resumo das leituras espectrais e incidentes recentes exibidos no aplicativo, bem como o texto da sua pergunta. Caso configure uma chave de API própria, ela é armazenada apenas localmente de forma criptografada via **Android Keystore**.

O tratamento de metadados de rede (como endereço IP) por esses provedores segue as políticas de privacidade de cada serviço (Google, Open-Meteo, Safecast e NOAA).

---

## 4. Armazenamento Local, Backup e Exportação

- **Armazenamento local:** Preferências da interface (`electric_eye_ui_prefs`), preferências da IA (`spectrum_ai_prefs`) e o histórico de alertas (`hazard_incidents.json`) são mantidos no armazenamento privado do aplicativo.
- **Proteção contra backup em nuvem:** O arquivo de histórico de incidentes (`hazard_incidents.json`) e as preferências de chave da IA (`spectrum_ai_prefs.xml`) são explicitamente excluídos do backup automático em nuvem e da transferência entre dispositivos (`backup_rules.xml` e `data_extraction_rules.xml`).
- **Relatórios PDF e CSV:** Arquivos gerados por você ficam em diretório de cache temporário e só são compartilhados via `FileProvider` quando você escolhe enviá-los por outro aplicativo.

---

## 5. Seus Controles e Exclusão de Dados

Você pode gerenciar e apagar seus dados diretamente:
- Desativando o envio de localização aproximada na opção **"Privacidade da Consulta Solar & Geiger"**;
- Limpando o histórico de alertas na aba de relatórios do aplicativo;
- Removendo sua chave de API personalizada nas configurações da IA;
- Revogando permissões nas configurações do sistema Android ou desinstalando o aplicativo (o que remove todos os dados armazenados localmente).

---

## 6. Público Infantil

O **Electric Eye** é um aplicativo educacional e técnico de instrumentação física ambiental, não direcionado a crianças menores de 13 anos, e não coleta intencionalmente dados pessoais de menores.

---

## 7. Aviso Técnico

O **Electric Eye** tem finalidade exclusivamente educacional e técnica para visualização de sensores físicos do ambiente. Não fornece diagnóstico médico e não substitui equipamentos certificados de metrologia ou dosimetria radiológica.

---

## 8. Alterações e Contato

Esta Política de Privacidade pode ser atualizada conforme a evolução do aplicativo, mantendo sempre a data da última revisão no topo desta página.

Para dúvidas, solicitações ou assuntos relacionados à privacidade:  
**Responsável:** Fabrício Vieira Sanfelice  
**Marca:** TradeVSan  
**E-mail:** suportetradevsan@gmail.com  
**Página oficial da política:** https://github.com/fabriciosanfelice-byte/ElectricEye
