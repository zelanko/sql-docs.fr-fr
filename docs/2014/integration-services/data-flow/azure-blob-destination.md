---
title: Azure Blob Destination | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobdest.f1
- sql11.dts.designer.afpblobdest.f1
ms.assetid: 820a1e7a-7182-4c7b-ab56-5b4097a7e042
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6f114f39d76a5ec764e9bab814123a668a522dbe
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52756861"
---
# <a name="azure-blob-destination"></a>Destination d’objet blob Azure
  Le composant **Destination d’objet blob Azure** permet à un package SSIS d’écrire des données dans un objet blob Azure. Les formats de fichier pris en charge sont : CSV et AVRO. Faites glisser le composant **Destination d’objet Blob Azure** au Concepteur de flux de données et double-cliquez dessus pour afficher l’éditeur).  
  
1.  Dans le champ **Gestionnaire de connexions Azure Storage** , spécifiez un gestionnaire de connexions Azure Storage existant ou créez-en un qui fera référence à un compte Azure Storage.  
  
2.  Dans le champ **Nom du conteneur d’objets blob** , spécifiez le nom du conteneur d’objets blob qui contient les fichiers sources.  
  
3.  Dans le champ **Nom de l’objet blob** , indiquez le chemin d’accès à l’objet blob.  
  
4.  Dans le champ **Format de fichier d’objet blob** , spécifiez le format d’objet blob à utiliser.  
  
5.  Si le format de fichier est CSV, vous devez renseigner le champ **Caractère séparateur de colonnes** . Sélectionnez également l’option **Noms de colonne dans la première ligne de données** si la première ligne du fichier contient des noms de colonne.  
  
6.  Après avoir spécifié les informations de connexion, basculez vers la page **Colonnes** pour mapper les colonnes sources sur les colonnes de destination pour le flux de données SSIS.  
  
  
