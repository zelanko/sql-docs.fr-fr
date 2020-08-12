---
title: Dépendances d'objet
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.common.objectdependencies.f1
ms.assetid: c63d1160-3f3d-45df-99be-6fe081125fb5
author: markingmyname
ms.author: maghan
ms.openlocfilehash: bdd7e624fea2f6c225c8839450e1d1d5f91a9de5
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86001924"
---
# <a name="object-dependencies"></a>Dépendances d'objet
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Certains objets de base de données possèdent des dépendances sur d'autres objets de base de données. Par exemple, les vues et les procédures stockées dépendent de l'existence de tables qui contiennent les données retournées par la vue ou la procédure. Les **Dépendances d'objets (page Général)** de l'objet actuel répertorient à la fois les objets de base de données indispensables au bon fonctionnement de l'objet et les objets qui dépendent de l'objet sélectionné. Un objet qui référence un autre objet dans sa définition et dont la définition est stockée dans le catalogue système est appelé une *entité de référence*. Un objet référencé par un autre objet est appelé *entité référencée*.  
  
Les **Dépendances d'objet (page Avancé)** de l'objet actuel répertorient les objets de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ainsi que les objets [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui dépendent de l'objet. Les objets peuvent être stockés sur des serveurs différents.  
  
Utilisez cette boîte de dialogue pour comprendre les dépendances avant de modifier ou de supprimer l'objet sélectionné.  
  
## <a name="ui-element-list"></a>Liste d’éléments d’interface utilisateur  
**Objets dépendant de** _\<selected object>_  
Cliquez sur ce bouton pour afficher la liste des objets dont les dépendances sont suivies et qui dépendent de l'objet sélectionné.  
  
**Objets dont**  _\<selected object>_ **dépend**  
Cliquez sur ce bouton pour afficher la liste des objets dont les dépendances sont suivies et dont dépend l'objet sélectionné.  
  
**Dépendances**  
Cliquez sur **Objets qui dépendent de** *<selected object>* pour afficher une vue hiérarchique des objets qui dépendent de l'objet sélectionné. Cliquez sur **Objets desquels** *<selected object>* **dépend** pour afficher une vue hiérarchique des objets dont dépend l'objet sélectionné.  
  
**Nom**  
Affiche le nom de l'objet sélectionné dans l'arborescence **Dépendances** affichée plus haut.  
  
**Type**  
Affiche le type de l'objet sélectionné dans l'arborescence **Dépendances** affichée plus haut.  
  
**Dernière heure de synchronisation**  
> [!NOTE]  
> Cette option est disponible uniquement dans la page **Avancé** .  
  
Spécifie l'heure et date de la dernière mise à jour des informations de dépendance.  
  
**Type de dépendance**  
> [!NOTE]  
> Cette option est disponible uniquement dans la page **Général** .  
  
Affiche le type de dépendance entre deux objets. Il peut s'agir d'une des méthodes suivantes :  
  
-   Dépendance liée au schéma  
  
    Relation entre deux objets qui empêche l'objet référencé d'être supprimé ou modifié tant que l'objet de référence existe. Une dépendance liée au schéma est créée lorsqu'une vue ou une fonction définie par l'utilisateur est créée à l'aide de la clause WITH SCHEMABINDING, lorsqu'une table référence un autre objet via une contrainte CHECK ou DEFAULT ou dans la définition d'une colonne calculée.  
  
-   Dépendance non liée au schéma  
  
    Relation entre deux objets qui n'empêche pas l'objet référencé d'être supprimé ou modifié.  
  
-   Entité non disponible ou non résolue  
  
    Indique le type de dépendance qui ne peut pas être déterminé. Cela se produit uniquement lorsque l'objet sélectionné est situé sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antérieure à [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
