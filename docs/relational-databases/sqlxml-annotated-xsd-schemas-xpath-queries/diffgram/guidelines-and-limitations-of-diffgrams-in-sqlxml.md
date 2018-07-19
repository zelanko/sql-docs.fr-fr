---
title: Instructions et Limitations de DiffGrams dans SQLXML | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: cf8689c4-2a63-4d05-b202-21b5ff187d7f
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 9f63bc4259d60cdca7a82057dacafad21573156a
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38051527"
---
# <a name="guidelines-and-limitations-of-diffgrams-in-sqlxml"></a>Instructions et limitations de DiffGrams dans SQLXML
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Souvenez-vous des éléments suivants lors de l'utilisation de DiffGrams avec SQLXML 4.0 :  
  
-   Types d’objet binaire volumineux (BLOB) tels que **text/ntext** et images ne doivent pas être utilisés dans le  **\<diffgr : avant >** bloquer lors de l’utilisation de DiffGrams, car cela les inclura pour une utilisation dans contrôle d’accès concurrentiel. Cela peut entraîner des problèmes avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en raison des limitations sur la comparaison pour les types BLOB. Par exemple, le mot clé LIKE est utilisé dans la clause WHERE pour effectuer une comparaison entre les colonnes de la **texte** de type de données ; Toutefois, les comparaisons échouent dans le cas des types d’objets BLOB où la taille des données est supérieure à 8 Ko.  
  
-   Caractères spéciaux dans **ntext** données peuvent entraîner des problèmes avec SQLXML 4.0 en raison des limitations sur la comparaison pour les types d’objets BLOB. Par exemple, l’utilisation de « [Serializable] » dans le  **\<diffgr : avant >** bloc d’un DiffGram, lorsqu’il est utilisé dans un contrôle d’une colonne de la concurrence **ntext** type échoue avec SQLOLEDB suivant description de l’erreur :  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
  
