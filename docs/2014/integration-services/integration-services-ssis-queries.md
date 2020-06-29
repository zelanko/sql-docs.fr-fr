---
title: Requêtes Integration Services (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Query Builder [Integration Services]
- queries [Integration Services]
- statements [Integration Services]
- queries [Integration Services], about queries in packages
ms.assetid: 8822bd29-4575-46c8-92a0-1a39bc2604c1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5ea5de1e9dacd6cce5c4e0b199d7220413da06d7
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85436286"
---
# <a name="integration-services-ssis-queries"></a>Requêtes Integration Services (SSIS)
  La tâche Exécution SQL, la source OLE DB, la destination OLE DB et la transformation de recherche peuvent utiliser des requêtes SQL. Dans la tâche d'exécution SQL, les instructions SQL peuvent créer, mettre à jour et supprimer des données et des objets de base de données, exécuter des procédures stockées et des instructions SELECT. Dans la source OLE DB et la transformation de recherche, les instructions SQL sont généralement des instructions SELECT ou EXEC. Cette dernière exécute le plus souvent des procédures stockées qui retournent des jeux de résultats.  
  
 Un requête peut être analysée pour déterminer si elle est valide. Pendant l’analyse d’une requête utilisant une connexion vers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], la requête est analysée, exécutée et le résultat de l’exécution (succès ou échec) est affecté au résultat de l’analyse. Si la requête utilise une connexion à des données qui ne sont pas [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], l'instruction est seulement analysée.  
  
 L'instruction SQL peut être définie soit en l'entrant directement dans le concepteur, soit en spécifiant une connexion de fichier ou une variable qui contient l'instruction.  
  
## <a name="direct-input-sql"></a>SQL à entrée directe  
 Le Générateur de requêtes est disponible dans l'interface utilisateur pour la tâche d'exécution SQL, la source OLE DB, la destination OLE DB et la transformation de recherche. Le générateur de requêtes présente les avantages suivants :  
  
-   Travailler visuellement ou avec des commandes SQL.  
  
     Le Générateur de requêtes comprend des volets graphiques qui composent visuellement votre requête et un volet de texte qui contient le texte SQL de votre requête. Vous pouvez travailler dans le volet graphique ou le volet de texte. Le Générateur de requêtes synchronise les vues afin de toujours faire correspondre le texte de la requête et la représentation graphique.  
  
-   Joindre des tables liées.  
  
     Si vous ajoutez plusieurs tables à votre requête, le générateur de requêtes détermine automatiquement la manière dont les tables sont associées entre elles et construit la commande de jointure appropriée.  
  
-   Interroger ou mettre à jour les bases de données.  
  
     Vous pouvez utiliser le générateur de requêtes pour renvoyer des données à l'aide d'instructions Transact-SQL SELECT, ou pour créer des requêtes qui mettent à jour, ajoutent ou suppriment des enregistrements dans une base de données.  
  
-   Afficher et modifier les résultats immédiatement.  
  
     Vous pouvez exécuter votre requête et travailler avec un jeu d'enregistrements dans une grille qui vous permet de faire défiler et de modifier les enregistrements de la base de données.  
  
 Bien que le générateur de requêtes soit limité visuellement à la création de requêtes SELECT, vous pouvez tapez le SQL pour d'autres types d'instructions, par exemple des instructions DELETE et UPDATE, dans le volet de texte. Le volet graphique est automatiquement mis à jour pour prendre en compte l'instruction SQL que vous avez tapée.  
  
 Vous pouvez également fournir une entrée directe en tapant la requête dans la boîte de dialogue de la tâche ou du composant de flux de données ou dans la fenêtre Propriétés.  
  
 Pour plus d’informations, consultez [Générateur de requêtes](../../2014/integration-services/query-builder.md).  
  
## <a name="sql-in-files"></a>SQL dans des fichiers  
 L'instruction SQL pour la tâche d'exécution SQL peut également se trouver dans un fichier distinct. Par exemple, vous pouvez écrire des requêtes à l'aide d'outils tels que l'éditeur de requêtes dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], enregistrer la requête dans un fichier, puis lire la requête à partir du fichier lors de l'exécution d'un package. Le fichier ne peut contenir que les instructions SQL à exécuter et des commentaires. Pour utiliser une instruction SQL stockée dans un fichier, vous devez fournir une connexion de fichiers qui spécifie le nom et l'emplacement du fichier. Pour plus d’informations, consultez [File Connection Manager](connection-manager/file-connection-manager.md).  
  
## <a name="sql-in-variables"></a>SQL dans des variables  
 Si la source de l'instruction SQL dans la tâche d'exécution SQL est une variable, vous fournissez le nom de la variable qui contient la requête. La propriété Value de la variable contient le texte de la requête. Vous définissez la propriété ValueType de la variable en tant que type de données String, puis vous tapez ou copiez l’instruction SQL dans la propriété Value. Pour plus d’informations, consultez [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md) et [Utiliser des variables dans des packages](../../2014/integration-services/use-variables-in-packages.md).  
  
  
