---
title: "Rechercher du texte avec des caractères génériques | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.wildcards
- vswildcardsbuilder
helpviewer_keywords:
- searches [SQL Server Management Studio], wildcards
- Query Editor [SQL Server Management Studio], wildcard searches
- wildcard options [SQL Server Management Studio]
ms.assetid: 449600f8-cc87-4b3f-878a-59c158a88a40
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c34c1db9c36da6e23375df861ed5a3ad6d2bd12f
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="search-text-with-wildcards"></a>Rechercher du texte avec des caractères génériques
  Les expressions ci-après peuvent remplacer des caractères ou des chiffres dans le champ **Rechercher** de la boîte de dialogue [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Find and Replace** dialog box.  
  
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
  
  
