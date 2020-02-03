---
title: Créer un rapport de tableau de base (didacticiel SSRS) | Microsoft Docs
ms.date: 04/16/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- walkthroughs [Reporting Services]
- tutorials [Reporting Services]
- reports [Reporting Services], creating
ms.assetid: 3b539b4b-26f2-4c0b-b506-80f175679a46
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: af41da75d553794019f1d01c8b8f5bb6aba80622
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "65103313"
---
# <a name="create-a-basic-table-report-ssrs-tutorial"></a>Créer un rapport de tableau de base (didacticiel SSRS)

Dans ce tutoriel, vous utilisez l’outil *Concepteur de rapports* dans Visual Studio / SQL Server Data Tools (SSDT). Vous créez un rapport paginé SQL Server Reporting Services (SSRS). Le rapport contient une table de requête, créée à partir des données de la base de données AdventureWorks2016.

Au cours de ce tutoriel, vous allez découvrir comment :
  
- Créer un projet de rapport.
- Configurer une connexion de données.
- Définir une requête.
- Ajouter une région de données de table.
- Mettre en forme le rapport.
- Regrouper et additionner des champs.
- Afficher un aperçu du rapport.
- Publier le rapport si vous le souhaitez.

## <a name="requirements"></a>Spécifications

Pour que vous puissiez suivre ce tutoriel, les composants suivants doivent être installés sur votre système :

- Moteur de base de données [!INCLUDE[msconame-md](../includes/msconame-md.md)] SQL Server.  
- SQL Server 2016 Reporting Services ou ultérieur (SSRS)
- La base de données AdventureWorks2016.  Pour plus d’informations, consultez [Exemples de bases de données AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases)
- [SQL Server Data Tools](../ssdt/download-sql-server-data-tools-ssdt.md) pour Visual Studio, ainsi que l’extension Reporting Services installée pour permettre l’accès au *Concepteur de rapports*
  
Vous devez également disposer d’autorisations en lecture seule pour pouvoir récupérer les données de la base de données AdventureWorks2016.

**Durée estimée pour effectuer ce didacticiel :** 30 minutes.

## <a name="next-steps"></a>Étapes suivantes

[Leçon 1 : Création d’un projet Report Server &#40;Reporting Services&#41;](lesson-1-creating-a-report-server-project-reporting-services.md)

[Leçon 2 : Spécification des informations de connexion &#40;Reporting Services&#41;](lesson-2-specifying-connection-information-reporting-services.md)

[Leçon 3 : Définition d’un dataset destiné à un rapport de table &#40;Reporting Services&#41;](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md)

[Leçon 4 : Ajout d’une table au rapport &#40;Reporting Services&#41;](lesson-4-adding-a-table-to-the-report-reporting-services.md)

[Leçon 5 : Mise en forme d’un rapport &#40;Reporting Services&#41;](lesson-5-formatting-a-report-reporting-services.md)

[Leçon 6 : Ajout d’un regroupement et de totaux &#40;Reporting Services&#41;](lesson-6-adding-grouping-and-totals-reporting-services.md)

## <a name="see-also"></a>Voir aussi

[Tutoriels sur Reporting Services](reporting-services-tutorials-ssrs.md) D’autres questions ? [Essayez de poser une question dans le forum Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231)
