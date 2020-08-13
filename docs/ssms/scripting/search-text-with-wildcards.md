---
title: Rechercher du texte avec des caractères génériques
description: Découvrez comment utiliser des caractères génériques dans le champ « Rechercher » d’une boîte de dialogue Rechercher et remplacer pour spécifier un modèle à mettre en correspondance.
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- vswildcardsbuilder
helpviewer_keywords:
- searches [SQL Server Management Studio], wildcards
- Query Editor [SQL Server Management Studio], wildcard searches
- wildcard options [SQL Server Management Studio]
ms.assetid: 449600f8-cc87-4b3f-878a-59c158a88a40
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c8e2766939038879d92de0f8f73b5c2eab38f45d
ms.sourcegitcommit: d855def79af642233cbc3c5909bc7dfe04c4aa23
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87122790"
---
# <a name="search-text-with-wildcards"></a>Rechercher du texte avec des caractères génériques
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
  Les expressions ci-après peuvent remplacer des caractères ou des chiffres dans le champ **Rechercher** de la boîte de dialogue **Rechercher et remplacer** de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-search-using-wildcards"></a>Pour effectuer une recherche avec des caractères génériques  
  
1.  Pour pouvoir utiliser des caractères génériques dans le champ **Rechercher** pendant des opérations Recherche rapide, **Rechercher dans les fichiers**, **Remplacement rapide**ou **Remplacer dans les fichiers** , sélectionnez l’option **Utiliser** sous **Options de recherche** , puis choisissez **Caractères génériques**.  
  
2.  Le bouton triangulaire **Générateur d'expressions** situé en regard du champ **Rechercher** devient alors disponible. Cliquez sur ce bouton pour afficher la liste des caractères génériques disponibles. Quand vous choisissez un élément dans le **Générateur d’expressions**, il est inséré dans la chaîne **Rechercher** .  
  
 Le tableau ci-dessous décrit les caractères génériques disponibles dans le **Générateur d’expressions**.  
  
|Expression|Syntaxe|Description|  
|----------------|------------|-----------------|  
|Tout caractère unique|?|Représente n'importe quel caractère unique.|  
|Tout chiffre|#|Représente n'importe quel chiffre unique. Par exemple, 7# représente les nombres incluant 7 suivi d'un autre nombre, tels que 71, mais pas 17.|  
|Caractères hors jeu|[! ]|Représente tout caractère ne figurant pas dans le jeu spécifié.|  
|Un ou plusieurs caractères|*|Représente n'importe quel caractère. Par exemple, nou* représente tout texte incluant « nou », tel que nouveaufichier.txt.|  
|Jeu de caractères|[ ]|Représente tout caractère du jeu de caractères spécifié.|  
  
## <a name="see-also"></a>Voir aussi  
 [Recherche et remplacement](../../relational-databases/scripting/search-and-replace.md)   
 [Rechercher du texte avec des expressions régulières](../../relational-databases/scripting/search-text-with-regular-expressions.md)  
