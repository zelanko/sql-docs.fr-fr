---
title: Instructions et Limitations de DiffGrams dans SQLXML | Documents Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: DiffGrams [SQLXML], about DiffGrams
ms.assetid: cf8689c4-2a63-4d05-b202-21b5ff187d7f
caps.latest.revision: "7"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 07f698a9bcd18566d4cca639e810056f79523684
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="guidelines-and-limitations-of-diffgrams-in-sqlxml"></a>Instructions et limitations de DiffGrams dans SQLXML
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]Lors de l’utilisation de DiffGrams avec SQLXML 4.0, n’oubliez pas les éléments suivants :  
  
-   Types d’objet binaire volumineux (BLOB) tels que **text, ntext** et les images ne doivent pas être utilisés dans les  **\<diffgr : avant >** bloquer lors de l’utilisation de DiffGrams, car cela les inclura pour une utilisation dans le contrôle d’accès concurrentiel. Cela peut entraîner des problèmes avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en raison des limitations sur la comparaison pour les types BLOB. Par exemple, le mot clé LIKE est utilisé dans la clause WHERE pour effectuer une comparaison entre les colonnes de la **texte** de type de données ; Toutefois, les comparaisons échouent dans le cas des types d’objets BLOB où la taille des données est supérieure à 8 Ko.  
  
-   Caractères spéciaux dans **ntext** de données peuvent entraîner des problèmes avec SQLXML 4.0 en raison des limitations sur la comparaison pour les types d’objets BLOB. Par exemple, l’utilisation de « [Serializable] » dans le  **\<diffgr : avant >** bloc d’un DiffGram, lorsqu’il est utilisé dans la vérification d’une colonne de l’accès concurrentiel **ntext** type échoue avec la description d’erreur SQLOLEDB suivante :  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
  
