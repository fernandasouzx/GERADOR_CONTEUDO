# Geração Automatizada de Conteúdo Criativo Multimodal com Llama 3 e Stable Diffusion XL

**Autora:** Fernanda Lima de Souza  
**Ambiente:** Google Colab  

## Resumo
Este projeto desenvolve um sistema para geração automatizada de conteúdo multimodal — texto e imagem — integrando o **Llama 3 8B Instruct** e o **Stable Diffusion XL (SDXL)** em um pipeline funcional e leve.  
A implementação foi feita em **Python**, diretamente no **Google Colab**, permitindo a criação de posts para redes sociais, descrições de produtos e e-mails de marketing, com personalização de tom, público e estilo visual.

Os principais objetivos incluem:
- Reduzir o consumo de memória com **quantização em 4 bits** e **offloading dinâmico**;
- Oferecer uma **interface interativa** com `ipywidgets`;
- Facilitar a integração entre **modelos de linguagem (LLMs)** e **modelos de difusão** para criação de conteúdo criativo.

---

## Arquitetura do Sistema

A arquitetura é composta por módulos independentes executados no Colab:

1. **Interface de Usuário**  
   - Desenvolvida com `ipywidgets`  
   - Permite configurar tipo de conteúdo, público, tom e palavras-chave.

2. **Configuração de Ambiente**  
   - Desinstala pacotes conflitantes e instala versões compatíveis de:
     ```
     torch==2.3.1+cu121
     transformers==4.41.2
     diffusers==0.29.0
     accelerate==0.30.1
     bitsandbytes==0.43.2
     ipywidgets==7.7.1
     ```
   - Inclui reinstalação forçada do `numpy` e limpeza de cache.

3. **Carregamento dos Modelos**
   - **Llama 3 8B Instruct:** para geração textual com quantização de 4 bits.  
   - **Stable Diffusion XL (Base + Refiner):** para geração e refinamento de imagens de alta resolução.

4. **Pipeline Multimodal**
   - Geração textual → Criação automática de prompt visual em inglês → Geração da imagem final.

---

## Otimizações de Execução

- **Quantização:** uso do `BitsAndBytesConfig` para reduzir VRAM.  
- **Offloading:** distribuição automática entre GPU e CPU com `accelerate`.  
- **Limpeza de Memória:** uso de `torch.cuda.empty_cache()` entre etapas.  
- **Execução fluida** mesmo em GPU T4 (~15 GB VRAM).

---

## Funcionalidades

- Geração textual com adaptação de estilo (Instagram, e-mail marketing, produto, roteiro curto etc.)  
- Criação automática de prompt visual otimizado para difusão.  
- Síntese de imagens em 1024×1024 com **SDXL Base + Refiner**.  
- Interface visual amigável em **tema escuro**.  

---

## Exemplo de Uso

### Cenário: Lançamento de Produto “OceanWave”
**Configurações:**
- Tipo de conteúdo: Post para Instagram  
- Produto: Tênis sustentável OceanWave  
- Público: Jovens adultos ecoconscientes  
- Tom: Entusiasmado  
- CTA: “Garanta o seu na pré-venda!”

**Resultado:**
- Texto coerente e engajante gerado pelo Llama 3  
- Prompt visual otimizado  
- Imagem fotorrealista produzida com SDXL

---

## Como Executar no Colab

1. Acesse o notebook no Google Colab.  
2. Execute a **Célula 1** para configurar o ambiente (instalação de dependências).  
3. Aguarde o carregamento dos modelos (Llama 3 + SDXL).  
4. Use a interface interativa para gerar conteúdo textual e visual.  
5. Visualize os resultados diretamente na saída da célula.

---

## Referências Principais

- **Meta AI.** [Llama 3: Open Foundation and Instruction Models (2024)](https://ai.meta.com/llama/)  
- **Stability AI.** [Stable Diffusion XL (2023)](https://huggingface.co/stabilityai/stable-diffusion-xl-base-1.0)  
- **Hugging Face.** [Transformers](https://huggingface.co/docs/transformers/index), [Diffusers](https://huggingface.co/docs/diffusers/index), [Accelerate](https://huggingface.co/docs/accelerate/index)  
- **Dettmers, T.** [BitsAndBytes](https://github.com/TimDettmers/bitsandbytes)  
- **Google.** [Google Colaboratory](https://colab.research.google.com/)  
- **PyTorch Foundation.** [PyTorch](https://pytorch.org/)  

---

## Conclusão

O projeto comprova a viabilidade de executar modelos generativos de ponta — como o **Llama 3** e o **SDXL** — em ambientes limitados como o Colab.  
A abordagem proposta equilibra **desempenho, usabilidade e eficiência**, tornando-se uma base sólida para futuras aplicações em automação de marketing, criação de conteúdo e design multimodal.
