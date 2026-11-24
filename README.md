# 🌌 Avengers: Doomsday (2026) — Experiência Cinematográfica em Modo Paisagem (Skia GPU)

Aplicação interativa cinematográfica em **React Native com Expo (100% compatível com Expo Go + TypeScript)** inspirada em **"AVENGERS: DOOMSDAY" (2026)**, utilizando:
- **`@shopify/react-native-skia`**: Renderização vetorial procedural acelerada na GPU (`SweepGradient`, `RadialGradient`, `LinearGradient`, `BlurMask`, `BackdropBlur`, `Shadow` com `inner`).
- **`react-native-reanimated`**: Animações a 60/120 FPS na UI Thread (`useSharedValue`, `useDerivedValue`, worklets nativas).
- **`react-native-gesture-handler`**: Navegação horizontal *parallax* por swipe (`Gesture.Pan`), toque (`Gesture.Tap`) e pressão longa (`Gesture.LongPress`).
- **`expo-screen-orientation`**: Travamento automático em **Modo Paisagem (`LANDSCAPE`)** ao abrir o app.
- **`expo-sensors` (`Gyroscope`)**: Reflexo metálico especular e parallax multicamadas controlados pela inclinação física do celular.
- **`expo-haptics`**: Feedback tátil sincronizado com cada poder e transição.

---

## 🖥️ Layout Dividido em Modo Paisagem (55% Palco | 45% Card Glassmorphism)

- **Lado Esquerdo (55% da largura):** Palco principal no `<Canvas>` do Skia onde fica o **emblema 3D/realista do personagem ou equipe**, matematicamente centralizado em `(cx, cy) = (stageWidth / 2, stageHeight / 2)` através de grupos locais na origem `(0, 0)` (garantindo **zero** desvios de alinhamento em qualquer resolução).
- **Lado Direito (45% da largura):** Card flutuante com efeito **vidro fosco (`<BackdropBlur blur={20}>`)** e borda metálica lapidada, exibindo:
  - Tag da equipe/facção e **Nome do Personagem/Equipe**.
  - **Curiosidade Oficial** (fatos reais dos quadrinhos da Marvel e da produção de *Avengers: Doomsday*).
  - Dica interativa do poder do emblema e indicador de navegação (*"Arraste para o lado para trocar • Toque no emblema para ativar"*).
- **Canto Superior Esquerdo (`Skia GPU FX: ON / OFF`):** Botão discreto para demonstração técnica em sala de aula (inicia em **OFF** para facilitar a comparação ao vivo), ligando/desligando gradientes metálicos, `SweepGradient`, `BlurMask`, `BackdropBlur` e partículas para comparar formas básicas 2D vs. gráficos realistas acelerados pela GPU.

---

## 🎬 Os 5 Slides Interativos

1. **AVENGERS: DOOMSDAY (Logo Oficial):**
   - **Visual & Fundo:** Névoa cósmica verde-esmeralda (`RadialGradient`) e runas arcanas flutuantes. Emblema metálico prateado `"A"` atravessando um anel chanfrado com aura verde brilhante (`BlurMask`).
   - **Interação:** Incline o celular para ver o reflexo metálico deslizar; toque para emitir uma onda de choque verde.
2. **DOUTOR DESTINO / VICTOR VON DOOM (Máscara Metálica):**
   - **Visual & Fundo:** Fundo sombrio com raios de magia arcana verde-esmeralda e máscara de aço escovado realista (com rebites metálicos, sombreamento 3D e olhos brilhando em verde intenso) emoldurada pelo capuz verde-escuro.
   - **Interação:** Segure o dedo na máscara para carregar energia arcana com vibração tátil (`expo-haptics`) e disparar raios verdes.
3. **QUARTETO FANTÁSTICO (Emblema "4" + Fogo & Campo de Força):**
   - **Visual & Fundo:** Fundo azul-cósmico com faíscas incandescentes de plasma laranja/amarelo subindo pela tela (Tocha Humana), malha hexagonal translúcida (Mulher Invisível) e o emblema circular `"4"` perfeitamente centralizado em `(0, 0) -> (cx, cy)`.
   - **Interação:** Arraste o dedo sobre o emblema para gerar rastros de chamas em tempo real na GPU.
4. **CAPITÃO AMÉRICA (Escudo de Vibranium Realista):**
   - **Visual & Fundo:** Fundo azul-marinho atmosférico com anéis concêntricos de metal escovado (`SweepGradient` cônico vermelho, prata, vermelho e núcleo azul) e a estrela prateada de 5 pontas calculada trigonometricamente com `Math.cos` e `Math.sin`.
   - **Interação:** Toque no escudo para fazê-lo girar em alta velocidade soltando faíscas cinéticas de impacto com vibração tátil.
5. **X-MEN (Emblema "X" + Garras de Adamantium):**
   - **Visual & Fundo:** Feixes de energia dourada e azul elétrico com o emblema circular `"X"` em relevo 3D metálico prateado e núcleo escuro.
   - **Interação:** Deslize o dedo diagonalmente sobre o emblema (ou toque) para criar **3 cortes brilhantes de garras de Adamantium** com faíscas metálicas que vão cicatrizando aos poucos.

---

## 🚀 Passo a Passo Seguro para Apresentar na Sala de Aula

> **Importante:** O app inicia com **Skia GPU FX: OFF** no canto superior esquerdo para você mostrar a versão simples primeiro e depois tocar no botão para ativar os efeitos de GPU ao vivo.

### 1. Verificar / Instalar o que pode faltar no PC da sala (Windows)
Abra o **PowerShell** (ou Terminal) e verifique se `git` e `node` estão instalados:

```powershell
node -v
npm -v
git --version
```

- **Se `node` não for reconhecido:** instale o Node.js LTS pelo `winget` (sem precisar abrir navegador):
  ```powershell
  winget install --id OpenJS.NodeJS.LTS -e --accept-package-agreements --accept-source-agreements
  ```
  *(Depois feche e abra o PowerShell novamente para atualizar o `PATH`).*
- **Se `git` não for reconhecido:** instale pelo `winget` ou baixe o ZIP direto no GitHub (`Code → Download ZIP`):
  ```powershell
  winget install --id Git.Git -e --accept-package-agreements --accept-source-agreements
  ```

### 2. Baixar o projeto e instalar dependências
```powershell
git clone https://github.com/niickcodes/avengers-doomsday-skia.git
cd avengers-doomsday-skia
npm install
```

*(Caso o `git` não esteja instalado e você tenha baixado o `.zip`, extraia a pasta, entre nela pelo terminal e rode apenas `npm install`).*

### 3. Iniciar o servidor para a turma escanear o QR Code
No terminal dentro da pasta do projeto, rode **com túnel** (funciona mesmo com os celulares nos dados móveis ou em Wi-Fi diferente):

```powershell
npx expo start --tunnel -c
```

- **Se pedir para instalar `@expo/ngrok`:** digite `y` e pressione Enter.
- **Mantenha essa janela do terminal aberta durante toda a apresentação** — se fechar o terminal, o QR Code para de responder.
- Peça para quem for testar abrir o app **Expo Go** (SDK 58 / versão `58.0.5`+) no celular e escanear o QR Code que apareceu no terminal.

### 4. Plano B (se o firewall da sala bloquear o `--tunnel`)
1. **Mesmo Wi-Fi (LAN):** Conecte o PC e o celular na mesma rede Wi-Fi (ou roteie a internet do seu celular para o PC) e rode:
   ```powershell
   npx expo start -c
   ```
2. **Direto da nuvem (`expo.dev`) no seu celular:** Abra o **Expo Go**, faça login na conta **`niickcodes`** e abra o projeto direto na aba **Home** (ou pelo QR Code de *Updates* no painel `expo.dev`) — não depende de servidor no PC.
