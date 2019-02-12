---
title: Instructions et Limitations de DiffGrams dans SQLXML | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: cf8689c4-2a63-4d05-b202-21b5ff187d7f
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2ce3283568cebebd81bc98b3d4ebba7ba81d46dd
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56041120"
---
# <a name="guidelines-and-limitations-of-diffgrams-in-sqlxml"></a>Instructions et limitations de DiffGrams dans SQLXML
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Souvenez-vous des éléments suivants lors de l'utilisation de DiffGrams avec SQLXML 4.0 :  
  
-   Types d’objet binaire volumineux (BLOB) tels que **text/ntext** et images ne doivent pas être utilisés dans le  **\<diffgr : avant >** bloquer lors de l’utilisation de DiffGrams, car cela les inclura pour une utilisation dans contrôle d’accès concurrentiel. Cela peut entraîner des problèmes avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en raison des limitations sur la comparaison pour les types BLOB. Par exemple, le mot clé LIKE est utilisé dans la clause WHERE pour effectuer une comparaison entre les colonnes de la **texte** de type de données ; Toutefois, les comparaisons échouent dans le cas des types d’objets BLOB où la taille des données est supérieure à 8 Ko.  
  
-   Caractères spéciaux dans **ntext** données peuvent entraîner des problèmes avec SQLXML 4.0 en raison des limitations sur la comparaison pour les types d’objets BLOB. Par exemple, l’utilisation de « [Serializable] » dans le  **\<diffgr : avant >** bloc d’un DiffGram, lorsqu’il est utilisé dans un contrôle d’une colonne de la concurrence **ntext** type échoue avec SQLOLEDB suivant description de l’erreur :  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
  
