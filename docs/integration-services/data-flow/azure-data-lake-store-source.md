---
title: "Source Azure Data Lake Store | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SQL13.DTS.DESIGNER.AFPADLSSRC.F1"
  - "sql14.dts.designer.afpadlssrc.f1"
ms.assetid: f9c3311f-7316-48d6-bf10-d810e70b4304
caps.latest.revision: 10
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# Source Azure Data Lake Store
  Le composant **Source Azure Data Lake Store** permet à un package SSIS de lire des données dans Azure Data Lake Store. Les formats de fichier pris en charge sont le format texte et Avro.
  
 **Source Azure Data Lake Store** est un composant de SQL Server Integration Services (SSIS) Feature Pack pour Azure pour SQL Server 2016. Le Feature Pack est disponible en téléchargement [ici](http://go.microsoft.com/fwlink/?LinkID=626967).  
  
>   [!NOTE] Pour que le gestionnaire de connexions Azure Data Lake Store et les composants qui l’utilisent, notamment la source Azure Data Lake Store et la destination Azure Data Lake Store, puissent se connecter aux services, veillez à télécharger la dernière version du Feature Pack Azure [ici](https://www.microsoft.com/download/details.aspx?id=49492). 
  
## <a name="configure-the-azure-data-lake-store-source"></a>Configurer la source Azure Data Lake Store
 1. Pour afficher l’éditeur de la source Azure Data Lake Store, faites glisser **Source Azure Data Lake Store** sur le concepteur de flux de données et double-cliquez dessus pour ouvrir l’éditeur.  
  
2.  Dans le champ **Gestionnaire de connexions Azure Data Lake Store**, spécifiez un gestionnaire de connexions Azure Data Lake Store existant ou créez-en un qui fait référence à un service Azure Data Lake Store.  
  
    1.  Dans le champ **Chemin d’accès au fichier**, spécifiez le chemin du fichier source dans Azure Data Lake Store.   
  
    2.  Dans le champ **Format de fichier**, spécifiez le format du fichier source.  
  
        Si le format de fichier est le format texte, vous devez renseigner le champ **Délimiteur de colonne**. Sélectionnez également l’option **Noms de colonne dans la première ligne de données** si la première ligne du fichier contient des noms de colonne.  
  
3.  Après avoir spécifié les informations de connexion, basculez vers la page **Colonnes** pour mapper les colonnes sources sur les colonnes de destination du flux de données SSIS.   