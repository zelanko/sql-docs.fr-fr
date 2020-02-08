---
title: Destination Azure Data Lake Store | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSDEST.F1
- sql14.dts.designer.afpadlsdest.f1
ms.assetid: 4c4f504f-dd2b-42c5-8a20-1a8ad9a5d632
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 952dcc604dd99c2563ee0c9ef6dac3b9980ce429
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "71293393"
---
# <a name="azure-data-lake-store-destination"></a>Destination Azure Data Lake Store

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Le composant **Destination Azure Data Lake Store** permet à un package SSIS d’écrire des données dans Azure Data Lake Store. Les formats de fichier pris en charge sont : Text, Avro et ORC. 
  
 **Destination Azure Data Lake Store** est un composant de [SQL Server Integration Services (SSIS) Feature Pack pour Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
 
> [!NOTE]
> Pour que le gestionnaire de connexions Azure Data Lake Store et les composants qui l’utilisent, notamment la source Azure Data Lake Store et la destination Azure Data Lake Store, puissent se connecter aux services, veillez à télécharger la dernière version du Feature Pack Azure [ici](https://www.microsoft.com/download/details.aspx?id=49492). 

**Configurer la destination Azure Data Lake Store**

1. Faites glisser le composant **Destination Azure Data Lake Store** vers le concepteur de flux de données et double-cliquez dessus pour visualiser l’éditeur.  

2.  Dans le champ **Gestionnaire de connexions Azure Data Lake Store** , spécifiez un gestionnaire de connexions Azure Data Lake Store existant ou créez-en un qui fait référence à un service Azure Data Lake Store.  
  
    1.  Dans le champ **Chemin du fichier** , spécifiez le nom du fichier où vous souhaitez écrire des données. Si ce fichier existe déjà, son contenu est remplacé.  
  
    2.  Dans le champ **Format de fichier** , spécifiez le format de fichier à utiliser.  
  
       Si le format de fichier est le format texte, vous devez renseigner le champ **Délimiteur de colonne** . Sélectionnez également l’option **Noms de colonne dans la première ligne de données** si la première ligne du fichier contient des noms de colonne.  

       Si le format de fichier est ORC, Java est nécessaire. Cliquez [ici](../../integration-services/azure-feature-pack-for-integration-services-ssis.md#dependency-on-java) pour obtenir des détails.
  
3.  Après avoir spécifié les informations de connexion, basculez vers la page **Colonnes** pour mapper les colonnes sources sur les colonnes de destination du flux de données SSIS.  
