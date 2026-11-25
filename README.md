# Alibi – Simulador de Perícia Criminal (Flutter)

Trabalho final de Código de Alta Performance Mobile.
Equipe: Kalyane Nayra Alves do Vale, Isabele e Isabelly.

## Como rodar
1. `flutter create alibi` (gera as pastas android/ios)
2. Substitua o `pubspec.yaml` e as pastas `lib/` e `assets/` pelas deste zip
3. `flutter pub get`
4. `flutter run --profile` (use um aparelho físico para medir desempenho)

## Estrutura
- `lib/models.dart` – modelos dos casos (JSON em `assets/cases.json`)
- `lib/state.dart` – ficha da perita e progresso (shared_preferences)
- `lib/game_state.dart` – regras da investigação (pontos, perguntas, análises)
- `lib/screens/` – splash, perfil, casos/dossiê, jogo, resultado
- `lib/config.dart` – chave `kOtimizado` (antes x depois)

## Otimizações aplicadas (para medir antes x depois)
1. **Isolate (`compute`)**: converte o JSON dos casos fora da thread de UI.
2. **RepaintBoundary + ValueNotifier**: a lanterna redesenha só o overlay (CustomPainter).
3. **ListView.builder + const**: chat e lista de casos constroem só o que aparece.
4. **Imagem otimizada** (`cacheWidth` na logo).
5. **Cache local** (shared_preferences): progresso offline.

Na tela inicial há o botão **Teste de desempenho**, com cargas grandes (4 MB de JSON, lista de 3.000 itens e chat de 5.000 mensagens) para medir antes x depois.

Dica: segure o título "Casos abertos" para ligar/desligar o overlay de FPS.
