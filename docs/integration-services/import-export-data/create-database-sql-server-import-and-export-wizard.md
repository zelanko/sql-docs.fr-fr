---
title: "Cr&#233;er la base de donn&#233;es (Assistant Importation et Exportation SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "02/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.impexpwizard.createdatabase.f1"
ms.assetid: 56a8a79f-086c-4bdc-8888-0045bb4b0cbf
caps.latest.revision: 54
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 52
---
# Cr&#233;er la base de donn&#233;es (Assistant Importation et Exportation SQL Server)
Si vous sélectionnez **Nouveau** dans la page **Choisir une destination** pour créer une base de données de destination SQL Server, l’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] présente la boîte de dialogue **Créer une base de données**. Dans cette page, spécifiez un nom pour la nouvelle base de données. Vous pouvez éventuellement modifier les paramètres de la taille initiale et la croissance automatique de la nouvelle base de données et de son fichier journal. 

> [!NOTE] Si vous recherchez des informations sur l’instruction CREATE DATABASE [!INCLUDE[tsql](../../includes/tsql-md.md)] et non sur la boîte de dialogue **Créer une base de données** de l’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md).  

## <a name="screen-shot-of-the-create-database-page"></a>Capture d’écran de la page Créer une base de données  
La capture d’écran suivante montre la boîte de dialogue **Créer une base de données** de l’Assistant.  

Cette boîte de dialogue de l’Assistant offre uniquement une partie des options disponibles pour la création d’une base de données SQL Server. Pour afficher et configurer toutes les options pour une nouvelle base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], utilisez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour créer ou configurer celle-ci. 

![Create database page of the Import and Export Wizard](../../integration-services/import-export-data/media/create-database.png "Create database page of the Import and Export Wizard")  

## <a name="provide-a-name-for-the-new-database"></a>Fournir un nom pour la nouvelle base de données  
**Nom**  
 Fournissez un nom unique pour la base de données SQL Server de destination. Veillez à respecter les conventions de nommage SQL Server quand vous nommez la base de données.  
  
-   Le nom de la base de données doit être unique au sein d’une instance de SQL Server.  
  
-   Le nom de la base de données peut avoir un maximum de 123 caractères. (5 caractères sont autorisés pour les suffixes que SQL Server ajoute au fichier de données et au fichier journal, ce qui ne dépasse pas du nombre maximum de 128 caractères.)  
  
-   Le nom de la base de données doit suivre les règles applicables aux identificateurs dans SQL Server. Voici les critères les plus importants.  
  
    -   Le premier caractère doit être une lettre, un trait de soulignement (_), une arobase (@), ou un signe dièse (#).  
  
    -   Les caractères qui suivent peuvent être des lettres, des chiffres, une arobase, un symbole dollar ($), un signe dièse ou un trait de soulignement.  
  
    -   Vous ne pouvez pas utiliser d’espaces ni d’autres caractères spéciaux.  
  
Pour obtenir des informations détaillées sur ces critères, consultez [Identificateurs de base de données](../../relational-databases/databases/database-identifiers.md).  

## <a name="optionally-specify-data-file-and-log-file-options"></a>Spécifiez éventuellement les options de fichier journal et de fichier de données

> [!TIP] Vous devez fournir un nom pour la nouvelle base de données dans le champ **Nom**, mais vous pouvez généralement laisser les autres paramètres de taille et de croissance de fichier avec leurs valeurs par défaut.
>
> Pour plus d’informations sur les options de taille de fichier que vous voyez sur cette page, consultez [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md). 

### <a name="data-file-options"></a>Options pour les fichiers de données  
 **Taille initiale**  
 Définissez le nombre de mégaoctets de la taille initiale du fichier de données.  
  
 **Aucune croissance autorisée**  
 Indiquez si la taille du fichier de données peut augmenter au-delà de la taille initiale spécifiée.  
  
 **Augmenter de (pourcentage)**  
 Définissez le pourcentage d'augmentation de la taille du fichier de données.  
  
 **Augmenter de (taille)**  
 Définissez le nombre d'octets d'augmentation de la taille du fichier de données.  
  
### <a name="log-file-options"></a>Options pour les fichiers journaux  
 **Taille initiale**  
 Définissez le nombre de mégaoctets de la taille initiale du fichier journal.  
  
 **Aucune croissance autorisée**  
 Indiquez si la taille du fichier journal peut augmenter au-delà de la taille initiale spécifiée.  
  
 **Augmenter de (pourcentage)**  
 Définissez le pourcentage d'augmentation du fichier journal.  
  
 **Augmenter de (taille)**  
 Définissez le nombre d'octets d'augmentation de la taille du fichier journal.  
  
## <a name="whats-next"></a>Étape suivante  
 Une fois que vous avez fourni un nom pour la nouvelle base de données que l’Assistant va créer et cliqué sur **OK**, la boîte de dialogue **Créer une base de données** vous renvoie à la page **Choisir une Destination**. Pour plus d’informations, consultez [Choisir une destination](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md).  
