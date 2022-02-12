# getstart-nanopore
Rough explanation  

## Recollection(感染症検査はなにをしてあげれるのか？)  

  * __マルチプレックスPCR__(クリニックレベルで)  [bioMérieux Japan](https://www.biomerieux-jp.net/clinical/c025.php)  
  * __DNAシークエンサー__  [ilumina](https://jp.illumina.com/systems/sequencing-platforms.html)  

## Oxford Nanopore Technologies(以下ONT).   [oxford nanopore](https://nanoporetech.com/)  
## なんでも、だれでも、どこでも  

  * 小さな機械.  [Minion](https://nanoporetech.com/products/minion)  
  * 核酸の塩基配列を読み取る. 
>"Why DNA/RNA?    
DNA and RNA are molecules that are present in all living things. DNA contains an organism’s genetic code, the instructions for building and operating an organism. RNA is primarily a messenger molecule, carrying instructions from the DNA code to control the synthesis of proteins – the building blocks of organisms.

>Sequencing is the process of identifying the order of ‘bases’ on a molecule of DNA or RNA. This is called a ‘sequence’.

>This sequence data can answer a range of biological questions such as ‘what is it?’ or ‘Is it healthy or diseased?’."   
>>なぜDNA / RNAなのか？   
DNAとRNAは、すべての生物に存在する物質です。DNAには、生物の遺伝情報、生物を構築および活動させるための指示が含まれています。RNAは主にメッセンジャー分子であり、生物の構成要素であるタンパク質の合成を制御するためのDNAコードからの指示を運びます。

>>シーケンシングは、DNAまたはRNAの分子の「塩基」の順番を特定するプロセスです。「シーケンス」と呼ばれます。

>>このシーケンスデータは、「それは何ですか？」のさまざまな生物学的質問に答えることができます。また「それは健康ですか、それとも病気ですか？」などにも。

## さらに
>"Pathogens / Microbiology.  
What is this virus/bacteria/fungus? What makes it pathogenic? Is it resistant to antimicrobial drugs? How could we use this information to prevent or treat the disease that it causes?"  

>>病原体/微生物学.  
このウイルス/細菌/真菌は何ですか？それは病原性がありますか？抗菌薬に耐性がありますか？この情報をどのように使用して、それが引き起こす病気を予防または治療できるでしょうか。　　　
## シークエンスまでの流れ(まずは16S rRNA sequence) [16S Barcoding Kit 1-24](https://store.nanoporetech.com/16s-barcoding-kit-1-24.html)  
![16S analysis using real-time, long-read nanopore sequencing](https://nanoporetech.com/sites/default/files/s3/16s-workflow3.svg "workflow")

   1. コロニーからDNAを抽出する  
   2. PCRをかける  
   3. アンプリコンをサイズセレクション  
   4. アダプターライゲーション  
   5. Minionでシークエンス  
   6. 解析  

## コロニーからDNAを抽出  
上記、ONTのworkflowではbead beating.  

現時点では以前から使用している試薬を使用。  [シカジーニアス® DNA抽出試薬](https://products.kanto.co.jp/web/index.cgi?c=t_product_table&pk=151)  
![操作手順](https://products.kanto.co.jp/products/siyaku/images/s_dna_photo1.jpg "dna_extraction_usage")  
  * 試薬bを8連PCRチューブに50uL分注しているものに1uL白金耳にてコロニーを釣菌。  
  * その後、試薬aを5uL入れサーマルサイクラーで加熱。  
  * 上清をテンプレートとして使用。  
## PCR
### 対象となる遺伝子領域である16srRNA領域を増幅し、さらに、`アダプター結合領域`と`バーコードを付加`する。  
#### PCR反応組成
    LongAmp Taq 2X Master Mix    25uL  
    16S Barcode Primers 01-24    7.25uL  
    template                    17.25uL  
    ________________________ up to 50uL  
## アンプリコンのサイズセレクション  
アンプリコン（PCR後の増幅した産物）をサイズセレクション（プライマーや伸長がうまくいかなかったものや短い配列のものを除去）する。  

   なぜ短い配列のものを排除するのか？  
   
     短い配列から読まれるため。  
     長い配列をたくさん読みたいため。  

### サイズセレクション magnetic rack
[AMPure XP](https://www.beckman.jp/reagents/genomic/cleanup-and-size-selection/pcr)  

![Ampure XP Beads](https://media.beckman.com/-/media/genomics/products/purification-and-cleanup/genomics-pcr-purification-agencourt-ampure-xp-2020-01.jpg?h=600&w=600&la=ja&hash=6344A913AC5FDE0F3DBFBB2E98509D944E2FD50A)
  1.  アンプリコンとAMPure　XP　Beads 30uLを混ぜて2分静置  
  2.  磁石で吸着　5分  
  3.  70%エタノールで洗浄  
  4.  上記を3回繰り返す  
  5.  エタノールを乾燥（〜30秒）  
  6.  Trisバッファー(10 mM Tris-HCl pH 8.0 with 50 mM NaCl)を15uL入れ５分静置
  7.  磁石で吸着　5分
  8.  上清を使用
### サイズセレクション　version Duo Prime  
[KingFisher Duo Prime](https://www.thermofisher.com/jp/ja/home/life-science/dna-rna-purification-analysis/automated-purification-extraction/kingfisher-systems/models/kingfisher-duo-prime.html)  
![Duo Prime](https://www.thermofisher.com/content/dam/tfsite/images/storefront/kingfisher/S/resized.jpg)  

