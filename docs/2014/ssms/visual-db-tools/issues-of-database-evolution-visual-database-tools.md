---
title: Problèmes liés à l’évolution d’une base de données (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- compatibility [SQL Server], multuser database changes
- database evolution [SQL Server]
ms.assetid: 1ed6ae10-d212-4ec2-8569-1b94ab1cba6d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 963ead996aaa38f13788c726338c7a83c28bb92d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48159239"
---
# <a name="issues-of-database-evolution-visual-database-tools"></a>Problèmes liés à l'évolution d'une base de données (Visual Database Tools)
  Si vous modifiez la structure d'une base de données déployée, assurez-vous que les changements sont compatibles avec les données existantes et la structure de la base de données. Il est quelquefois nécessaire de prendre des mesures spéciales si les modifications appartiennent à une des catégories suivantes :  
  
-   **Ajout d’une contrainte** Quand vous ajoutez une contrainte, la base de données contient peut-être déjà des données qui ne la respectent pas. Quand vous essayez d’enregistrer la nouvelle contrainte, la [boîte de dialogue Notifications post-enregistrement &#40;Visual Database Tools&#41;](visual-database-tools.md) vous informe que le serveur de base de données n’a pas pu la créer. Pour obliger la base de données à accepter la nouvelle contrainte, vous pouvez décocher la case **Vérifier les données existantes à la création**.  
  
-   **Ajout d’une relation** Quand vous ajoutez une relation, la base de données contient peut-être déjà dans la table de clés étrangères des lignes sans correspondance dans la table de clés primaires. Ce qui signifie que les données existantes ne respectent peut-être pas l'intégrité référentielle. Quand vous essayez d’enregistrer la nouvelle relation, la [boîte de dialogue Notifications post-enregistrement &#40;Visual Database Tools&#41;](visual-database-tools.md) vous informe que le serveur de base de données n’a pas pu enregistrer la table de clé étrangère révisée. Pour obliger la base de données à accepter la modification, vous pouvez décocher la case **Vérifier les données existantes à la création**.  
  
-   **Modification d’une table contribuant à une vue indexée** Si vous modifiez une table contribuant à une vue Microsoft SQL Server indexée, vous perdez les index de la vue. Pour plus d'informations sur la reconstitution d'index, consultez la documentation en ligne de SQL Server.  
  
-   **Suppression d’un objet** Si vous supprimez un objet, tel qu’une colonne, une table ou une vue, vérifiez d’abord qu’il n’est pas référencé par un autre objet dans la base de données.  
  
 Quelle que soit la façon dont vous modifiez le design de la base de données, gardez un historique de ces modifications. Une méthode consiste à conserver des scripts SQL de toutes les modifications que vous avez apportées à la base de données de production.  
  
## <a name="see-also"></a>Voir aussi  
 [Contraintes uniques et les contraintes Check](../../relational-databases/tables/unique-constraints-and-check-constraints.md)   
 [Environnements multi-utilisateurs &#40;Visual Database Tools&#41;](multiuser-environments-visual-database-tools.md)  
  
  
