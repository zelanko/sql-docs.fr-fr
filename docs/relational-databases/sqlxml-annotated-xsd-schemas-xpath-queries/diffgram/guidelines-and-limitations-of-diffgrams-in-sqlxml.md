---
title: Instructions et limitations de DiffGrams dans SQLXML
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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 113090c317e88d3e9a7e7db2bfcb7d4d14b4ea1f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85650065"
---
# <a name="guidelines-and-limitations-of-diffgrams-in-sqlxml"></a>Instructions et limitations de DiffGrams dans SQLXML
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  Souvenez-vous des éléments suivants lors de l'utilisation de DiffGrams avec SQLXML 4.0 :  
  
-   Les types d’objets BLOB (Binary Large Object) tels que **text/ntext** et images ne doivent pas être utilisés dans le **\<diffgr:before>** bloc dans lors de l’utilisation de DiffGrams, car cela les inclura pour une utilisation dans le contrôle d’accès concurrentiel. Cela peut entraîner des problèmes avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en raison des limitations sur la comparaison pour les types BLOB. Par exemple, le mot clé LIKE est utilisé dans la clause WHERE pour la comparaison entre les colonnes du type de données **Text** ; Toutefois, les comparaisons échouent dans le cas de types d’objets BLOB où la taille des données est supérieure à 8 Ko.  
  
-   Les caractères spéciaux dans les données **ntext** peuvent engendrer des problèmes avec SQLXML 4,0 en raison des limitations de comparaison pour les types d’objets BLOB. Par exemple, l’utilisation de « [Serializable] » dans le **\<diffgr:before>** bloc d’un DiffGram lorsqu’il est utilisé dans le contrôle d’accès concurrentiel d’une colonne de type **ntext** échoue avec la description d’erreur SQLOLEDB suivante :  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
  
