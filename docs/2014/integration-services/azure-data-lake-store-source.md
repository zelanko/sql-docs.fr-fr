---
title: Source Azure Data Lake Store | Microsoft Docs
ms.custom: ''
ms.date: 06/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSSRC.F1
- SQL11.DTS.DESIGNER.AFPADLSSRC.F1
ms.assetid: 7d9e8457-62aa-4aea-98ee-7d1121dfae4f
author: yualan
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2037890618a4977135d6366d8d84bb84a9c67744
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48129432"
---
# <a name="azure-data-lake-store-source"></a>Source Azure Data Lake Store
  Le composant **Source Azure Data Lake Store** permet à un package SSIS de lire des données dans Azure Data Lake Store. Les formats de fichier pris en charge sont le format texte et Avro.
  
## <a name="configure-the-azure-data-lake-store-source"></a>Configurer la source Azure Data Lake Store 
  
1.  Pour afficher l’éditeur de la source Azure Data Lake Store, faites glisser **Source Azure Data Lake Store** sur le concepteur de flux de données et double-cliquez dessus pour ouvrir l’éditeur.  
  
2.  Dans le champ **Gestionnaire de connexions Azure Data Lake Store** , spécifiez un gestionnaire de connexions Azure Data Lake Store existant ou créez-en un qui fait référence à un service Azure Data Lake Store.  
  
    1.  Dans le champ **Chemin d’accès au fichier** , spécifiez le chemin du fichier source dans Azure Data Lake Store.   
  
    2.  Dans le champ **Format de fichier** , spécifiez le format du fichier source.  
  
        Si le format de fichier est le format texte, vous devez renseigner le champ **Délimiteur de colonne** . Sélectionnez également l’option **Noms de colonne dans la première ligne de données** si la première ligne du fichier contient des noms de colonne.  
  
3.  Après avoir spécifié les informations de connexion, basculez vers la page **Colonnes** pour mapper les colonnes sources sur les colonnes de destination du flux de données SSIS.  
