---
title: Destination Azure Data Lake Store | Microsoft Docs
ms.custom: ''
ms.date: 06/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSDEST.F1
- SQL11.DTS.DESIGNER.AFPADLSDEST.F1
ms.assetid: d0e86032-2a6b-48b2-898f-e94328474fde
author: yualan
ms.author: chugu
ms.openlocfilehash: 14248d14b6a944250c33a19c8cf83ab0e0330587
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439416"
---
# <a name="azure-data-lake-store-destination"></a>Destination Azure Data Lake Store
  Le composant **Destination Azure Data Lake Store** permet à un package SSIS d’écrire des données dans Azure Data Lake Store. Les formats de fichier pris en charge sont les formats texte, Avro et ORC. 
  
## <a name="configure-the-azure-data-lake-store-destination"></a>Configurer la destination Azure Data Lake Store 

1. Faites glisser le composant **Destination Azure Data Lake Store** vers le concepteur de flux de données et double-cliquez dessus pour visualiser l’éditeur.  

2.  Dans le champ **Gestionnaire de connexions Azure Data Lake Store** , spécifiez un gestionnaire de connexions Azure Data Lake Store existant ou créez-en un qui fait référence à un service Azure Data Lake Store.  
  
    1.  Dans le champ **Chemin du fichier** , spécifiez le nom du fichier où vous souhaitez écrire des données. Si ce fichier existe déjà, son contenu est remplacé.  
  
    2.  Dans le champ **Format de fichier** , spécifiez le format de fichier à utiliser.  
  
        Si le format de fichier est le format texte, vous devez renseigner le champ **Délimiteur de colonne** . Sélectionnez également les **noms de colonne dans la première ligne de données** si la première ligne du fichier contient des noms de colonnes.  

        Si le format de fichier est ORC, vous devez installer l’environnement JRE de la plateforme correspondante. 
  
3.  Après avoir spécifié les informations de connexion, basculez vers la page **Colonnes** pour mapper les colonnes sources sur les colonnes de destination du flux de données SSIS.  
