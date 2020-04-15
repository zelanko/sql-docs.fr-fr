---
title: Drop TABLE Command ( Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- drop table command [ODBC]
ms.assetid: bc50459b-8861-4889-84a9-129ae9065aa8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 779c519f720027aea3a6f6cf2587d3c6e0b59b52
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303420"
---
# <a name="drop-table-command"></a>DROP TABLE, commande
Supprime une table de la base de données spécifiée avec la source de données et la supprime du disque.  
  
 Le Visual FoxPro ODBC Driver prend en charge la syntaxe en langue visuelle FoxPro native pour cette commande. Pour obtenir des renseignements spécifiques au conducteur, consultez les remarques.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP TABLE TableName | FileName | ?  
```  
  
## <a name="settings"></a>Paramètres  
 *TableName*  
 Spécifie la table à supprimer de la base de données spécifiée avec la source de données et à supprimer du disque.  
  
 *FileName*  
 Spécifie une table gratuite à supprimer du disque.  
  
 ?  
 Affiche le dialogue Supprimer à partir duquel vous pouvez choisir une table à supprimer de la base de données spécifiée avec la source de données et supprimer du disque.  
  
## <a name="remarks"></a>Notes  
 Lorsque DROP TABLE est émis, tous les index primaires, les valeurs par défaut et les règles de validation associés à la table sont également supprimés. DROP TABLE affecte également d’autres tableaux de la base de données spécifiés avec la source de données si ces tableaux ont des règles ou des relations associées à la suppression du tableau. Les règles et les relations ne sont plus valides lorsque la table est supprimée de la base de données.  
  
## <a name="driver-remarks"></a>Remarques du conducteur  
 Lorsque votre application envoie la table DROP TABLE DROP à la source de données, le visual FoxPro ODBC Driver convertit la commande en commande Visual FoxProDROP TABLE à l’aide de la syntaxe indiquée dans le tableau suivant.  
  
|Syntaxe ODBC|Source de données|Syntaxe visuelle FoxPro|  
|-----------------|-----------------|--------------------------|  
|DROP TABLE *base-table-nom*|Base de données (.dbc fichier)|SUP TABLE *NomMe* DELETE|  
||Annuaire des tables gratuites (.dbf fichiers)|EFFACER *dbfName*<br /><br /> ERASE *cdxName*<br /><br /> ERASE *fptName*|
