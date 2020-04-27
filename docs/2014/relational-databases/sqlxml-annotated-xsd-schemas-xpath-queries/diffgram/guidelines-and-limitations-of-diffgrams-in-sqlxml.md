---
title: Instructions et limitations des DiffGrams dans SQLXML | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: cf8689c4-2a63-4d05-b202-21b5ff187d7f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a1113bf11fcb3b1be2164bc6e685e6454323f3df
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66013059"
---
# <a name="guidelines-and-limitations-of-diffgrams-in-sqlxml"></a>Instructions et limitations de DiffGrams dans SQLXML
  Souvenez-vous des éléments suivants lors de l'utilisation de DiffGrams avec SQLXML 4.0 :  
  
-   Les types de données BLOB tels que `text/ntext` et les images ne doivent pas être utilisés dans le bloc `<diffgr:before>` lors de l'utilisation de DiffGrams, car cela les inclura dans le contrôle d'accès concurrentiel. Cela peut entraîner des problèmes avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en raison des limitations sur la comparaison pour les types BLOB. Par exemple, le mot clé LIKE est utilisé dans la clause WHERE pour effectuer une comparaison entre les colonnes du type de données `text` ; toutefois, les comparaisons échouent dans le cas de types BLOB lorsque la taille des données dépasse 8 Ko.  
  
-   Les caractères spéciaux dans les données `ntext` peuvent entraîner des problèmes avec SQLXML 4.0 en raison des limitations sur la comparaison pour les types BLOB. Par exemple, l'utilisation de "[Serializable]" dans le bloc `<diffgr:before>` d'un DiffGram, s'il est utilisé dans le contrôle d'accès concurrentiel d'une colonne de type `ntext`, échouera avec la description d'erreur SQLOLEDB suivante :  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
  
