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
- **Canto Superior Esquerdo (`Skia GPU FX: ON / OFF`):** Botão discreto para demonstração técnica em sala de aula, desligando gradientes metálicos, `SweepGradient`, `BlurMask`, `BackdropBlur` e partículas para comparar formas básicas 2D vs. gráficos realistas acelerados pela GPU.

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

## 🚀 Como Executar no Expo Go

```powershell
cd "C:\Users\Nick\.gemini\antigravity\scratch\avengers-skia-poster"
npx expo start -c
```
Abra o **Expo Go** no seu smartphone e escaneie o QR Code — o aplicativo travará automaticamente em modo paisagem (*landscape*).
