---
description: UPDATE, instruction - limitations
title: Limitations des instructions UPDATE | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- UPDATE statement limitations [ODBC]
- ODBC SQL grammar, UPDATE statement limitations
ms.assetid: 14700aac-e135-4dc0-9138-4b01224461d5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b7c1ea2e5e9d887005084cdb5454dcf9b5e8fa24
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471398"
---
# <a name="update-statement-limitations"></a>UPDATE, instruction - limitations
Pour que le pilote Paradox met à jour une table, la table doit avoir un index unique (clé primaire Paradox). Lorsque vous utilisez le pilote Paradox sans implémenter le Moteur de base de données Borland, il n’est pas possible de mettre à jour une table Paradox.  
  
 Non pris en charge par le pilote de texte.  
  
 Lorsque le pilote Microsoft Excel est utilisé, il est possible de mettre à jour les valeurs, mais une ligne ne peut pas être supprimée d’une table basée sur une feuille de calcul Microsoft Excel. Par conséquent, l’instruction UPDATE n’est pas considérée comme officiellement prise en charge par le pilote Microsoft Excel. Seule l’instruction INSERT est considérée comme prise en charge.
