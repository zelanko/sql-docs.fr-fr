---
title: Propriétés du catalogue de texte intégral (page général) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftcatalogproperties.general.f1
ms.assetid: d1f66762-2d40-4f24-b635-a417d22ee79a
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 60a56b6d64957198292146d392ea22a572fb8a4e
ms.sourcegitcommit: 4b5919e3ae5e252f8d6422e8e6fddac1319075a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2020
ms.locfileid: "83000959"
---
# <a name="full-text-catalog-properties-general-page"></a>Propriétés du catalogue de texte intégral (page Général)
  Cette section présente les options et fonctions disponibles dans la page **Général** de la boîte de dialogue **Propriétés du catalogue de texte intégral** .  
  
> [!NOTE]  
>  Pour les bases de données [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] , un catalogue de texte intégral est un concept logique qui fait référence à un groupe d'index de recherche en texte intégral. Le catalogue de texte intégral est un objet virtuel qui n'appartient à aucun groupe de fichiers.  
  
## <a name="options"></a>Options  
  
### <a name="properties"></a>Propriétés  
 **Catalogue par défaut**  
 Indique si le catalogue est le catalogue par défaut de la base de données.  
  
 **État du remplissage**  
 Indique l'état du catalogue. Les valeurs possibles sont les suivantes :  
  
-   **Inactif**  
  
-   **Analyse en cours**  
  
-   **En pause**  
  
-   **Throttled**  
  
-   **la récupération**  
  
-   **Arrêt**  
  
-   **Remplissage incrémentiel en cours**  
  
-   **Construction des index**  
  
-   **Le disque est en pause plein**  
  
-   **Suivi des modifications**  
  
 **Nombre d’éléments**  
 Affiche le nombre d'éléments de texte intégral contenus dans le catalogue.  
  
 **Taille du catalogue**  
 Affiche la taille en mégaoctets du catalogue de texte intégral.  
  
 **Nom**  
 Nom du catalogue de texte intégral.  
  
 **Respecter les accents**  
 Affichez ou modifiez si le catalogue est sensible aux marques diacritiques, telles qu’un tilde ( **~** ), un accent aigu (**́**) ou un tréma (**̈**). Les valeurs autorisées sont :  
  
-   **Non**  
  
-   **Oui**  
  
-   Pour plus d’informations sur les signes diacritiques, consultez [diacritiques](https://www.merriam-webster.com/dictionary/diacritic) dans le dictionnaire Merriam-Webster.  
  
 **Date du dernier remplissage**  
 Affiche la date du dernier remplissage du catalogue.  
  
 **Propriétaire**  
 Propriétaire du catalogue de texte intégral.  
  
 **Nombre de clés uniques**  
 Nombre de mots uniques qui constituent l'index de texte intégral du catalogue.  
  
### <a name="catalog-action"></a>Action du catalogue  
  
|||  
|-|-|  
|**Aucun**|N'exécute aucune opération de type **Optimiser le catalogue**, **Reconstruire le catalogue**ou **Remplir à nouveau le catalogue** .|  
|**Optimiser le catalogue**|Optimise l'utilisation de l'espace du catalogue et améliore les performances des requêtes. Cette option améliore également la précision du classement de la pertinence des résultats de la recherche.<br /><br /> Cette action exécute ALTER FULLTEXT CATALOG *catalog_name* REORGANIZE.|  
|**Reconstruire le catalogue**|Supprime et reconstruit le catalogue de texte intégral. Cette opération doit être exécutée si une propriété fondamentale du catalogue a été modifiée (par exemple, le respect des accents).<br /><br /> Pour que la reconstruction réussisse, le groupe de fichiers dans lequel réside le catalogue de texte intégral doit être en ligne ou accessible en lecture et en écriture. Après la reconstruction, l'index de texte intégral sera rempli à nouveau.<br /><br /> Cette action exécute ALTER FULLTEXT CATALOG *catalog_name* REBUILD.|  
|**Remplir à nouveau le catalogue**|Met à jour le catalogue avec les modifications récemment apportées aux données. Cette option ne requiert aucun temps mort du catalogue.|  
  
## <a name="see-also"></a>Voir aussi  
 [Alimenter des index de recherche en texte intégral](../relational-databases/indexes/indexes.md)  
  
  
