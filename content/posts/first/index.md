---
title: "Java 25: o que mudou (guia para iniciantes)"
description: "Um resumo simples e direto das principais novidades do Java 25, com exemplos e dicas práticas para quem está começando."
categories: ["tech"]
tags: ["java", "jdk", "jdk25", "novidades"]
date: 2025-10-27
publishDate: 2025-10-27
---

{{< lead >}}🚀 Chegou o Java 25! Neste post, eu explico de forma simples o que mudou, por que isso importa para você e mostro exemplos práticos que você pode copiar e colar.{{< /lead >}}

{{< alert >}}
Nota de transparência: este guia resume as principais áreas de evolução do Java 25 (linguagem, performance/GC, bibliotecas e ferramentas) de forma prática para iniciantes. Verifique sempre as notas oficiais de lançamento para detalhes e JEPs específicos do 25: [openjdk.org/projects/jdk/25](https://openjdk.org/projects/jdk/25).
{{< /alert >}}

## Resumo rápido (em 1 minuto) ✨
- Linguagem mais expressiva: pattern matching, records e melhorias em `switch` continuam estáveis e úteis no dia a dia.
- Performance: avanços contínuos em GCs modernos (como ZGC) e otimizações de runtime/JIT.
- Biblioteca padrão: APIs mais consistentes e utilitários de qualidade de vida.
- Ferramentas: melhorias no ecossistema (`jlink`, `jpackage`, build e diagnósticos).
- Deprecações/remoções: verifique release notes ao atualizar para evitar surpresas.

## O que isso significa para você 🧭
Para quem está começando, a boa notícia é que o Java moderno está mais simples de escrever e manter. Recurso como pattern matching e virtual threads ajudam a tornar o código claro e eficiente sem complicar o aprendizado.

## Mudanças na linguagem, na prática 🧩

1) Pattern Matching com `switch` e Records Patterns

Permite “desestruturar” objetos de forma segura e expressiva.

```java
record Point(int x, int y) {}

static String descreve(Object obj) {
    return switch (obj) {
        case Point(int x, int y) when x == y -> "ponto na diagonal";
        case Point(int x, int y) -> "ponto (" + x + ", " + y + ")";
        case String s -> "texto: " + s;
        case null -> "nulo";
        default -> "desconhecido";
    };
}
```

2) Strings mais práticas ([preview] em algumas versões recentes)

Templates de string facilitam concatenação e interpolação de valores.

```java
// Recurso em evolução; pode exigir flag: --enable-preview
String name = "Aline";
int stars = 5;
String result = STR."Olá, \{name}! Você ganhou \{stars} ⭐";
System.out.println(result);
```

## Concorrência mais simples com Virtual Threads 🧵

Virtual Threads ajudam a lidar com muitas tarefas I/O em paralelo com código simples.

```java
import java.util.stream.IntStream;
import java.util.concurrent.Executors;

public class App {
    public static void main(String[] args) throws Exception {
        try (var executor = Executors.newVirtualThreadPerTaskExecutor()) {
            IntStream.range(0, 100).forEach(i ->
                executor.submit(() -> {
                    Thread.sleep(50);
                    System.out.println("Olá do VT " + i);
                    return i;
                })
            );
        }
    }
}
```

Por que isso é legal?
- Escala melhor em I/O do que threads de plataforma.
- Código continua “sequencial” e fácil de entender.

## Performance e GC ⚙️
- Otimizações contínuas em ZGC/G1 reduzem pausas e melhoram throughput em cargas modernas.
- Melhorias no JIT/AOT e no runtime ajudam aplicações a iniciar mais rápido e consumir menos recursos.

## Biblioteca padrão 📦
- Pequenas adições e ajustes melhoram ergonomia (coleções, IO/NIO, utilitários de tempo, etc.).
- Sempre confira as notas de alteração para APIs que ganharam métodos novos ou comportamentos mais previsíveis.

## Deprecações e remoções 🧹
- Versões recentes costumam marcar APIs antigas para remoção futura. Ao atualizar, rode seus testes e verifique warnings de compilação.

## Como migrar com segurança ✅
1. Leia as release notes do JDK 25 (mudanças, JEPs, deprecações).
2. Atualize o JDK localmente e rode a suíte de testes.
3. Ative flags de pré-visualização apenas se precisar e com consciência.
4. Monitore métricas (memória, pausas de GC, tempo de inicialização) após a atualização.

## Links úteis 🔗
- Projeto JDK 25: [openjdk.org/projects/jdk/25](https://openjdk.org/projects/jdk/25)
- JEPs: [openjdk.org/jeps/0](https://openjdk.org/jeps/0)
- Downloads: [jdk.java.net](https://jdk.java.net)
