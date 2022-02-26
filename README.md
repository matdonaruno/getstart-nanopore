# getstart-nanopore
（agenda） A brief description of Nanopore

## Recollection(感染症検査はなにをしてあげれるのか？)  

  * __マルチプレックスPCR__(クリニックレベルで)  [bioMérieux Japan](https://www.biomerieux-jp.net/clinical/c025.php)  
  * __DNAシークエンサー__  [ilumina](https://jp.illumina.com/systems/sequencing-platforms.html)  

## いままでの菌種同定の難しさ  
<img src="https://user-images.githubusercontent.com/18117653/155849877-da93d426-e0ad-44f4-816d-9a8c597cbec7.jpeg" width="200"><img src="https://user-images.githubusercontent.com/18117653/155850017-367636f3-9541-45e3-b9f6-06b2d77c15c5.jpeg" width="200">

 * WalkAway マイクロスキャンパネル[マイクロスキャン WalkAway Plus](https://jaclas.or.jp/Product/index?id=79317)

 * 同定キット[細菌同定検査キット　アピ/ID32 シリーズ](https://www.biomerieux-jp.net/clinical/c023.php)
 * 同定キット[BD BBLCRYSTAL™](https://www.bd.com/ja-jp/offerings/capabilities/microbiology-solutions/industrial-microbiology/systems-for-rapid-check-for-industrial-microbiology/bbl-crystal-identification-system)

## 無難な質量分析装置[MALDI-TOF](https://www.bruker.com/ja/products-and-solutions/mass-spectrometry/maldi-tof.html)

価格は・・・

## なにが必要か。

 * どんな微生物でも同定できること
 * 手技が一定であること
 * 発育が困難な微生物・発育が遅い微生物でも早く同定できること
 * 抗菌薬選択の情報が取得できること

## Oxford Nanopore Technologies(以下ONT).   [oxford nanopore](https://nanoporetech.com/)  
## なんでも、だれでも、どこでも  

  * 小さな機械.  [MinION](https://nanoporetech.com/products/minion)  ,  [Nanopore products](https://nanoporetech.com/products)
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

## nanopooreの原理  
How nanopore sequence works(https://www.youtube.com/watch?v=RcP85JHLmnI)   
Introduction to nanopore sequence(https://www.youtube.com/watch?v=qzusVw4Dp8w)

## シークエンスまでの流れ(まずは16S rRNA sequence) [16S Barcoding Kit 1-24](https://store.nanoporetech.com/16s-barcoding-kit-1-24.html)  
![16S analysis using real-time, long-read nanopore sequencing](https://nanoporetech.com/sites/default/files/s3/16s-workflow3.svg "workflow")  
[16S analysis using real-time, long-read nanopore sequencing](https://nanoporetech.com/analyse/16s)  

   1. コロニーからDNAを抽出する  
   2. PCRをかける  
   3. アンプリコンをサイズセレクション  
   4. DNA定量、検体プール
   5. アダプターライゲーション  
   6. Minionでシークエンス  
   7. 解析  

## コロニーからDNAを抽出  
上記、ONTのworkflowではbead beating.  

現時点では以前から使用している試薬を使用。  [シカジーニアス® DNA抽出試薬](https://products.kanto.co.jp/web/index.cgi?c=t_product_table&pk=151)  
![操作手順](https://products.kanto.co.jp/products/siyaku/images/s_dna_photo1.jpg "dna_extraction_usage")  
  * 試薬bを8連PCRチューブに50uL分注しているものに1uL白金耳にてコロニーを釣菌。  
<img src="" width="200"><img src="" width="200">
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

### サイズセレクション version magnetic rack
[AMPure XP](https://www.beckman.jp/reagents/genomic/cleanup-and-size-selection/pcr)  

<img src="https://media.beckman.com/-/media/genomics/products/purification-and-cleanup/genomics-pcr-purification-agencourt-ampure-xp-2020-01.jpg?h=600&w=600&la=ja&hash=6344A913AC5FDE0F3DBFBB2E98509D944E2FD50A" width="200">

  1.  アンプリコンとAMPure　XP　Beads 30uLを混ぜて2分静置  
<img src="" width="200">  
  2.  磁石で吸着　5分  
<img src="" width="200">  
  3.  70%エタノール 200uLで洗浄  
  4.  上記を3回繰り返す  
  5.  エタノールを乾燥（〜30秒）  
  6.  Trisバッファー(10 mM Tris-HCl pH 8.0 with 50 mM NaCl)を15uL入れ５分静置
  7.  磁石で吸着　5分
  8.  上清を使用  

### サイズセレクション　version Duo Prime  

[KingFisher Duo Prime](https://www.thermofisher.com/jp/ja/home/life-science/dna-rna-purification-analysis/automated-purification-extraction/kingfisher-systems/models/kingfisher-duo-prime.html)  

![Duo Prime](https://www.thermofisher.com/content/dam/tfsite/images/storefront/kingfisher/S/resized.jpg)  

プレートの準備
deep wellに試薬を入れる  
[KingFisher™ Plastics for 96 deep-well format](https://www.thermofisher.com/order/catalog/product/95040450)  
![96 deep-well](https://assets.thermofisher.com/TFS-Assets/BID/product-images/KF%2096%20deep-well%20plate.jpeg-250.jpg)  
  *  A列にAMPure XP beadsを30uL
  *  C,D列に70%エタノールを200uL
  *  Elusion stripにTrisバッファーを35uL
  *  A列にアンプリコンを全量50uL入れる
  *  Duo Primeの「16s library cleanup」でスタート  

## DNA定量 version multiscansky
[Thermo Scientific™ Multiskan SkyHigh Microplate Spectrophotometer](https://www.thermofisher.com/order/catalog/product/A51119500C#/A51119500C)  

<img src="https://assets.thermofisher.com/TFS-Assets/BID/product-images/3-Multiskan%20SkyHigh%20alone-TF%202017%2005%20-26-650x600.jpg-650.jpg" width="200">

[UV-Star, 384ウェル, マイクロプレート](https://shop.gbo.com/ja/japan/products/bioscience/microplates/uv-star-microplates/384-well-uv-star-microplates/781801.html)

<img src="https://shop.gbo.com/ja/japan/images/16097175/781801_01.jpg" width="200">


  *  プレートに各アンプリコンを30uL入れる  
  *  Multiskan Skyで「nanopore DNA check」で測定  
  *  各アンプリコンの濃度を100ngになるように1.5mLチューブにプールしていく  
  *  プールしたライブラリーを5uLを別の1.5uLチューブへ移す  
  *  kit付属のRAPを0.33uL混ぜて室温５分反応させる  
  *  そこにkit付属のSequencing Buffer 12.5uLとLoading Beads 15.5uLを混ぜる  
  *  ライブラリーの完成！

## フローセルのプライミング  
## フローセルへのライブラリーのロード  
## シークエンス  
## フローセルの洗浄  
