---
title: Représentation des jointures par le concepteur de requêtes et de vues (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL pane [Visual Database Tools]
- joins [SQL Server], Query and View Designer
- Diagram pane [Visual Database Tools]
ms.assetid: 20a99dcb-83bd-4aa6-9139-92e2e5ba4887
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: abd8dd7c3c23a13b1cdff7a2d6f76fb99375a641
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63155258"
---
# <a name="how-the-query-and-view-designer-represents-joins-visual-database-tools"></a>Représentation des jointures dans le Concepteur de requêtes et de vues (Visual Database Tools)
  Dans le cas de tables jointes, le [Concepteur de requêtes et de vues](visual-database-tools.md) représente la jointure graphiquement dans le [volet Schéma](diagram-pane-visual-database-tools.md) et il utilise la syntaxe SQL dans le [volet SQL](sql-pane-visual-database-tools.md).  
  
## <a name="diagram-pane"></a>Volet Schéma  
 Dans le volet Schéma, le Concepteur de requêtes et de vues affiche une ligne de jointure entre les colonnes de données impliquées. Il affiche une ligne de jointure par condition de jointure. Par exemple, l'illustration suivante montre une ligne de jointure entre deux tables jointes :  
  
 ![La ligne de jointure illustre la relation entre deux tables](../../database-engine/media//dv3wbig.gif "La ligne de jointure illustre la relation entre deux tables")  
  
 Si des tables ont plusieurs conditions de jointure, le Concepteur de requêtes et de vues affiche plusieurs lignes de jointure, comme l'illustre l'exemple suivant :  
  
 ![Tables jointes à l'aide de plusieurs conditions de jointure](../../database-engine/media//dv3w9n1.gif "Tables jointes à l'aide de plusieurs conditions de jointure")  
  
 Si les colonnes de données jointes ne sont pas affichées (parce que, par exemple, le rectangle représentant la table ou l'objet table est réduit ou la jointure implique une expression), le Concepteur de requêtes et de vues place la ligne de jointure dans la barre de titre du rectangle représentant la table ou l'objet structuré en table.  
  
 La forme de l'icône au milieu de la ligne de jointure indique la façon dont les tables ou les objets structurés en table sont joints. Si la clause de jointure utilise un autre opérateur que le signe égal (=), il apparaît dans l’icône de la ligne de jointure. Le tableau suivant fait la liste des icônes qui apparaissent dans la ligne de jointure.  
  
|**Icône de la ligne de jointure**|**Description**|  
|------------------------|---------------------|  
|![Icône Visual Database Tools](../../database-engine/media//dv3wbih.gif "Icône Visual Database Tools")|Jointure interne (créée avec un opérateur « égal »).|  
|![Icône Visual Database Tools](../../database-engine/media//dv3wbii.gif "Icône Visual Database Tools")|Jointure interne basée sur l'opérateur « plus grand que ».|  
|![Icône Visual Database Tools](../../database-engine/media//dv3wbij.gif "Icône Visual Database Tools")|Jointure externe dans laquelle toutes les lignes de la table représentée à gauche seront incluses, même si elles n'ont pas de correspondance dans la table en relation.|  
|![Icône Visual Database Tools](../../database-engine/media//dv3wbik.gif "Icône Visual Database Tools")|Jointure externe dans laquelle toutes les lignes de la table représentée à droite seront incluses, même si elles n'ont pas de correspondance dans la table en relation.|  
|![Icône Visual Database Tools](../../database-engine/media//dv3wbil.gif "Icône Visual Database Tools")|Jointure externe entière dans laquelle toutes les lignes des deux tables seront incluses, même si elles n'ont pas de correspondance dans la table en relation.|  
  
 Les symboles présents aux extrémités de la ligne de jointure indiquent le type de jointure. Le tableau suivant fait la liste des types de jointures et des icônes affichées aux extrémités de la ligne de jointure.  
  
|**Icône aux extrémités de la ligne de jointure**|**Type de jointure**|  
|-----------------------------------|----------------------|  
|![Icône Visual Database Tools](../../database-engine/media//dv3wbim.gif "Icône Visual Database Tools")|Jointure Un-à-un.|  
|![Icône Visual Database Tools](../../database-engine/media//dv3wbin.gif "Icône Visual Database Tools")|Jointure Un-à-plusieurs.|  
|![Icône Visual Database Tools](../../database-engine/media//dv3wbio.gif "Icône Visual Database Tools")|Le Concepteur de requêtes et de vues ne peut pas déterminer le type de jointure. Ce cas s'observe surtout lorsque vous avez créé une jointure manuellement.|  
  
## <a name="sql-pane"></a>volet SQL  
 Dans une instruction SQL, une jointure peut être exprimée de plusieurs façons différentes. La syntaxe exacte dépend de la base de données utilisée et de la façon dont la jointure a été définie.  
  
 Pour spécifier une jointure de tables, vous disposez de plusieurs options de syntaxe :  
  
-   **Qualificateur de jointure pour la clause from**.   Les mots clés INNER et OUTER spécifient le type de jointure. Il s'agit de la syntaxe standard du SQL ANSI 92.  
  
     Par exemple, si vous joignez les tables `publishers` et `pub_info` sur la base de la colonne `pub_id` de chaque table, vous obtenez une instruction SQL similaire à la suivante :  
  
    ```  
    SELECT *  
    FROM publishers INNER JOIN pub_info ON  
       publishers.pub_id = pub_info.pub_id  
    ```  
  
     En cas de jointure externe, le mot INNER est remplacé par les mots LEFT OUTER ou RIGHT OUTER.  
  
-   La **clause WHERE compare les colonnes des deux tables**.   Une clause WHERE apparaît si la base de données ne prend pas en charge la syntaxe JOIN (ou si vous l'avez entrée vous-même). Si la jointure est créée dans la clause WHERE, les noms des deux tables apparaissent dans la clause FROM.  
  
     Par exemple, l'instruction suivante joint les tables `publishers` et `pub_info` .  
  
    ```  
    SELECT *  
    FROM publishers, pub_info  
    WHERE publishers.pub_id = pub_info.pub_id  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Interroger avec des jointures &#40;Visual Database Tools&#41;](query-with-joins-visual-database-tools.md)   
 [Boîte de dialogue Joindre &#40;Visual Database Tools&#41;](join-dialog-box-visual-database-tools.md)  
  
  
