# 🔍 Code Review Criativo
Creative Code Review Practices / Code Review Criativo

> **Disciplina:** Criatividade — Aula 05 | 29/04/2026  
> **Curso:** Análise e Desenvolvimento de Sistemas — TADS25.109/2N  
> **Instituição:** SENAC Recife-PE  
> **Docente:** Prof. Guibson Santana  
> **Discentes:** Thayná Batista da Silva · Polyana Fontes

---

## 📌 Sobre a Técnica

O **Code Review Criativo** é uma abordagem de revisão colaborativa de código que vai além da aprovação superficial ("LGTM 👍"). Em vez de verificar apenas se o código funciona, o revisor atua de forma criativa: faz perguntas investigativas, simula cenários extremos, propõe alternativas e compartilha conhecimento — transformando a revisão em um momento de aprendizado mútuo.

| Campo | Informação |
|---|---|
| **Nome** | Code Review Criativo |
| **Origem** | Engenharia de Software (práticas ágeis e open source) |
| **Conceito** | Revisão intencional e colaborativa de código com postura criativa e crítica |
| **Objetivo** | Elevar qualidade do código, identificar bugs/vulnerabilidades e promover aprendizado |
| **Por que é criativa?** | Questiona abordagens, propõe alternativas e transforma erros em oportunidades |
| **Plataformas** | Web, Mobile, Desktop, APIs, Microsserviços, IA/ML — qualquer contexto colaborativo |

---

## 🧪 Exemplo Prático

### Problema Original

```python
# Código com problemas – Code Review necessário
def calcular_desconto(preco, percentual):
    desconto = preco * percentual / 100
    preco_final = preco - desconto
    return preco_final

print(calcular_desconto(-100, 10))   # Retorna -90 (preço negativo!)
print(calcular_desconto(200, 110))   # Retorna -20 (preço negativo!)
print(calcular_desconto(0, 50))      # Retorna 0 (sem validação)
```

### Perguntas Criativas da Revisão

- "O que acontece se o preço informado for negativo?"
- "E se o percentual de desconto ultrapassar 100%?"
- "O código trata o caso de preço zero?"
- "O preço final pode ser negativo? Qual é o comportamento esperado?"

### Código Refatorado após Code Review Criativo

```python
# ✅ Versão refatorada após Code Review Criativo
def calcular_desconto(preco: float, percentual: float) -> float:
    """
    Calcula o preço final com desconto aplicado.
    Parâmetros validados: preço > 0, percentual entre 0 e 100.
    """
    if preco <= 0:
        raise ValueError("O preço deve ser maior que zero.")

    if not (0 <= percentual <= 100):
        raise ValueError("O percentual deve estar entre 0 e 100.")

    desconto = preco * (percentual / 100)
    return round(preco - desconto, 2)

print(calcular_desconto(200, 10))   # 180.0
print(calcular_desconto(99.99, 5))  # 94.99
```

---

## 🔄 Síntese do Processo

| Etapa | Descrição |
|---|---|
| **Problema inicial** | Função sem validações que aceitava entradas inválidas e retornava preços negativos |
| **Técnica utilizada** | Code Review Criativo com questionamento ativo e simulação de casos extremos |
| **Raciocínio estimulado** | Pensamento defensivo, pensamento de borda e pensamento colaborativo |
| **Resultado obtido** | Código validado, documentado, com tratamento de erros e arredondamento correto |

---

## 💡 Aprendizados

- Revisar código criativamente vai além de procurar erros: é uma oportunidade de compartilhar conhecimento
- Perguntas abertas e simulação de cenários extremos são mais eficazes que validar apenas se o código roda
- Comentários encorajadores tornam o processo mais produtivo e menos intimidador
- O Code Review Criativo pode ser aplicado profissionalmente em qualquer equipe que use pull requests
- Ferramentas de IA (CodeRabbit, GitHub Copilot) complementam, mas não substituem, o olhar criativo humano

---

## 📚 Referência

PATEL, Riyana. **Beyond 'LGTM': Creative Code Review Practices That Actually Work**.  
DEV Community / PullFlow, 2025.  
Disponível em: <https://dev.to/pullflow/beyond-lgtm-creative-code-review-practices-that-actually-work-58jg>

JOSHI, Shreyas. **AI + Code Review + GitHub Copilot** [Publicação profissional].  
LinkedIn, 2025.  
Disponível em: <https://www.linkedin.com/posts/shreyas-joshi-166987215_ai-codereview-githubcopilot-activity-7390669382135316480-E4xl/>

---

> *"Todo código compila com lógica, mas só evolui quando alguém ousa pensá-lo diferente."*  
> — Prof. Guibson Santana
