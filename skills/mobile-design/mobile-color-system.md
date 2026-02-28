# Referência do Sistema de Cores Mobile

> Otimização OLED, modo escuro, cores conscientes da bateria e visibilidade externa.
> **Cor no mobile não é apenas estética — trata-se de vida útil da bateria e usabilidade.**

---

## 1. Fundamentos de Cores Mobile

### Por que a cor no mobile é diferente

```
DESKTOP:                           MOBILE:
├── Telas LCD (backlit)            ├── Telas OLED comuns (emissão própria)
├── Iluminação controlada          ├── Ambiente externo, sol forte
├── Energia estável                ├── A bateria importa
├── Preferência pessoal            ├── Modo escuro em todo o sistema
└── Visualização estática          └── Ângulos variáveis, movimento
```

---

## 2. Considerações de OLED

### Como o OLED se diferencia

```
OLED (Organic LED):
├── Cada pixel emite sua própria luz
├── Preto = pixel DESLIGADO (zero energia)
├── Consumo de energia = pixels mais brilhantes consomem mais
└── Modo escuro = economia significativa de bateria
```

### Preto Real (True Black) vs Quase Preto (Near Black)

- **#000000 (Preto Real)**: Economia máxima de bateria. Pode causar "black smear" ao rolar a tela. Recomendado pela Apple.
- **#121212 ou #1A1A1A (Quase Preto)**: Rolagem mais suave, menos cansativo para os olhos. Recomendado pelo Material Design.

---

## 3. Design em Modo Escuro

### Estratégia de Cores para Modo Escuro

- **Background**: #000000 ou #121212.
- **Superfície**: #1E1E1E escalando para #3C3C3C em elevações maiores.
- **Texto Primário**: Use tons de branco acinzentado (#E0E0E0), nunca branco puro contra preto puro para evitar ofuscamento.
- **Cores Primárias**: Devem ser dessaturadas para evitar o efeito de "brilho excessivo" em fundos escuros.

---

## 4. Visibilidade Externa (Outdoor)

### O Problema da Luz Solar
A luz do sol "lava" contrastes baixos. Use contrastes altos (mínimo 4.5:1, idealmente 7:1+). Evite tons pastéis e gradientes sutis para informações críticas quando o usuário estiver em ambiente externo.

---

## 5. Cores Semânticas

| Semântica | Significado | Padrão iOS | Padrão Android |
| :--- | :--- | :--- | :--- |
| **Erro** | Problemas, destruição | #FF3B30 | #B3261E |
| **Sucesso** | Conclusão, positivo | #34C759 | #4CAF50 |
| **Aviso** | Atenção, cuidado | #FF9500 | #FFC107 |
| **Info** | Informação | #007AFF | #2196F3 |

**Regra**: Nunca use cores semânticas apenas para decoração ou marca. Combine sempre com ícones para usuários daltônicos.

---

## 6. Cor Dinâmica (Android)

### Material You
O Android 12+ extrai cores do papel de parede do usuário para criar o tema do app. Suporte isso sempre que possível em Android, mantendo cores de marca apenas onde for estritamente necessário.

---

## 7. Acessibilidade de Cores

### Considerações para Daltônicos
- Cerca de 8% dos homens são daltônicos.
- **Nunca dependa apenas da cor** para transmitir significado (ex: erro no formulário). Use ícones ou texto de suporte.

---

## 8. Anti-Padrões de Cores

- ❌ **Cinza claro sobre branco**: Invisível sob o sol.
- ❌ **Branco puro no modo escuro**: Cansa a vista.
- ❌ **Mesma saturação no modo escuro**: As cores parecem "neon" e agressivas.
- ❌ **Roxo/Violeta como padrão**: **BANIDO** (evite aparência genérica de IA).

---

## 9. Checklist do Sistema de Cores

### Antes de escolher cores
- [ ] Variantes de modo claro e escuro definidas?
- [ ] Contrastes verificados (mínimo 4.5:1)?
- [ ] Bateria OLED considerada?
- [ ] Seguro para daltônicos (não usa apenas cor)?

---

## 10. Referência Rápida

### Backgrounds no Modo Escuro
- **Preto Real (OLED)**: #000000
- **Quase Preto (Material)**: #121212
- **Superfície 1**: #1E1E1E
- **Superfície 2**: #2C2C2C

### Contrastes
- Texto pequeno: 4.5:1 (mínimo)
- Texto grande: 3:1 (mínimo)
- Ideal (AAA): 7:1

---

> **Lembre-se:** A cor no mobile deve funcionar nas piores condições — sol forte, olhos cansados, daltonismo, bateria baixa. Cores bonitas que falham nestes testes são cores inúteis.
