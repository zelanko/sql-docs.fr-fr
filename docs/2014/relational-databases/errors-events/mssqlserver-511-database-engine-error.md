---
title: MSSQLSERVER_511 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 511 (Database Engine error)
ms.assetid: 0c85686a-53c1-4180-ba8c-2000e68a0d63
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ee53135fb492185d91287f553b7b1f0ddf3cc8ba
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62867794"
---
# <a name="mssqlserver511"></a>MSSQLSERVER_511
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|511|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|ROW_TOOBIG|  
|Texte du message|Impossible de créer une ligne de dimension %d supérieure au maximum autorisé %d.|  
  
## <a name="explanation"></a>Explication  
 L'opération que vous avez tentée a dépassé la taille maximale d'une ligne. Habituellement, la taille maximale d'une ligne est 8 060 octets. Certains formats de stockage contiennent une surcharge susceptible de réduire la taille de ligne disponible pour les données. Par exemple, lorsque vous utilisez des colonnes éparses, la taille maximale d'une ligne est 8 018 octets. Certaines opérations qui ajoutent ou suppriment des lignes et certaines opérations qui modifient le type de données d'une colonne exigent que la ligne soit réécrite dans la page de données et que la ligne d'origine soit ensuite supprimée. Dans ces opérations, la limite effective de la taille de la ligne correspond à la moitié de la limite maximale. Cela est dû au fait que la ligne d'origine et la ligne modifiée doivent toutes les deux être incluses dans la page de données pour une courte période.  
  
> [!WARNING]  
>  Chaque colonne **varchar(max)** ou **nvarchar(max)** non Null demande 24 octets d’allocation fixe supplémentaire calculée par rapport à la limite de 8 060 octets par ligne pendant une opération de tri. Cela peut produire une limite implicite du nombre de colonnes **varchar(max)** ou **nvarchar(max)** non Null pouvant être créées dans une table. Aucune erreur spéciale n'est fournie quand la table est créée (mis à part l’avertissement habituel indiquant que la taille maximale de ligne dépasse la taille maximale autorisée de 8 060 octets) ou quand les données sont insérées. Cette grande taille de ligne peut provoquer des erreurs (comme l’erreur 512) au cours des opérations normales, telles que la mise à jour de la clé d’index cluster ou le tri de l’intégralité des colonnes, que les utilisateurs ne peuvent pas anticiper tant qu’elles n’ont pas été effectuées.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Si cela est possible, réduisez la taille de la ligne.  
  
 Si vous pensez que le problème provient d'une mise à jour sur place de la ligne, vous devez modifier la table en plusieurs étapes. Créez une nouvelle table et transférez les données dans la nouvelle table. Ensuite, supprimez la table d'origine et renommez la nouvelle table, ou tronquez la table d'origine, modifiez les lignes dans la table d'origine, puis replacez les données dans cette table.  
  
  
