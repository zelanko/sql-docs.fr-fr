---
description: Ajouter des éléments existants à un projet
title: Ajouter des éléments existants à un projet
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], item additions
- adding project items
ms.assetid: 084b3879-e96b-45a7-b421-6a4b0db2b92b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 3744d99ede7e4f50e7fb4393d8e58cff314f4f06
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88480112"
---
# <a name="add-existing-items-to-a-project"></a>Ajouter des éléments existants à un projet
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Vous pouvez ajouter des éléments à un projet pour étendre la fonctionnalité de l'application. Un élément existant peut être une requête ou un fichier divers. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] comporte deux types de projets : les projets de script [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les projets de script Analysis Services. Les fichiers de requête que vous pouvez ajouter au projet sont déterminés par le type du projet. Par exemple, vous pouvez ajouter une requête [!INCLUDE[tsql](../../includes/tsql-md.md)] (fichier doté de l'extension .sql) à un projet de script [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , mais vous ne pouvez pas l'ajouter à un projet de script de services d'analyse. Pour associer d’autres extensions de fichier à un type de projet, consultez [Procédure : associer des extensions de fichier à un éditeur de code](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md).  
  
### <a name="to-add-an-existing-query-or-a-miscellaneous-file-to-a-project"></a>Pour ajouter une requête existante ou un fichier divers à un projet  
  
1.  Dans l'Explorateur de solutions, sélectionnez un projet cible.  
  
2.  Dans le menu **Projet** , cliquez sur **Ajouter un élément existant**.  
  
    **Look in**  
    Recherche les fichiers ou dossiers à ajouter au projet dans cette liste. Pour les services Web XML et les applications Web ASP.NET, les fichiers se trouvent sur un serveur Web.  
  
    **Bureau**  
    Affiche les fichiers et les dossiers situés sur le bureau.  
  
    **Mes projets**  
    Affiche les fichiers et les dossiers à l’emplacement **Mes projets** par défaut.  
  
    **Poste de travail**  
    Affiche le contenu du dossier **Poste de travail** .  
  
    **Nom de fichier**  
    Utilisez cette option pour filtrer les fichiers et les dossiers affichés. Entrez une partie ou l'intégralité du nom de fichier servant de filtre. Vous pouvez utiliser l'astérisque (`*`) comme caractère générique.  
  
    > [!NOTE]  
    > Vous pouvez naviguer jusqu’à un emplacement sur le web ou sur le réseau en entrant une URL ou un chemin réseau dans la zone de texte **Nom de fichier** . Par exemple, **`https://mywebsite`** affiche les fichiers disponibles à l’emplacement monsiteweb, tandis que **\\\myserver\myshare** affiche les fichiers disponibles à l’emplacement partage sur monserveur.  
  
    **Type de fichiers**  
    Utilisez cette option pour filtrer les fichiers selon leur extension de fichier. Chaque produit affiche la liste des filtres par défaut correspondant aux types de fichiers les plus courants.  
  
    **Ajouter**  
    Utilisez ce bouton déroulant pour ajouter l'élément au projet et ouvrez l'élément dans son éditeur par défaut.  
  
    -   **Ajouter**  
  
        Copie l'élément existant dans le dossier de votre projet sur le disque et ajoute l'élément au projet sélectionné dans l'Explorateur de solutions. Aucune modification apportée à l'élément n'est répercutée à l'emplacement d'origine. Il s'agit de l'éditeur par défaut pour le type de fichier.  
  
    -   **Ajouter comme lien**  
  
        Ajoute le fichier sélectionné au projet et l'ouvre avec l'éditeur par défaut pour le type de fichier. Cette option ouvre le fichier sélectionné à l'origine et ne copie pas le fichier dans le dossier du projet.  
  
3.  Si vous ajoutez des fichiers de requête, la boîte de dialogue de connexion vous invite à spécifier une connexion pour la requête. Vous pouvez cliquer sur **Annuler** dans la boîte de dialogue de connexion si vous ne souhaitez pas associer de connexion à la requête.  
  
4.  Le fichier est ajouté au dossier **Requêtes** ou **Fichiers divers** du projet.  
  
## <a name="see-also"></a>Voir aussi  
[Explorateur de solutions](../../ssms/solution/solution-explorer.md)  
[Ajouter de nouveaux éléments à un projet](../../ssms/solution/add-new-items-to-a-project.md)  
[Enlever ou supprimer un élément ou un projet](../../ssms/solution/remove-or-delete-an-item-or-project.md)  
  
