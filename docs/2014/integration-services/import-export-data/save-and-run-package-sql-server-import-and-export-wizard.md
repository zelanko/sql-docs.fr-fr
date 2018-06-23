---
title: Enregistrez et exécutez le Package (SQL Server Assistant Importation et exportation) | Documents Microsoft
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.impexpwizard.saveschedule.f1
ms.assetid: b582c462-3d7a-4a4c-a2a2-2c79fedab75a
caps.latest.revision: 39
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 6071acee5eb7d888bdf4182a30f433e531754f64
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051299"
---
# <a name="save-and-execute-package-sql-server-import-and-export-wizard"></a>Enregistrer et exécuter le package (Assistant Importation et Exportation SQL Server)
  Utilisez le **enregistrer et exécuter le Package** boîte de dialogue pour exécuter le package immédiatement, enregistrement qu’il s’exécute ultérieurement, ou les deux.  
  
> [!NOTE]  
>  Si vous arrêtez un package avant la fin de son exécution, le package n’est pas enregistré, même si vous avez sélectionné le **enregistrer** case à cocher.  
  
 Pour en savoir plus sur cet Assistant, consultez [SQL Server Assistant Importation et exportation](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Pour en savoir plus sur les options de démarrage de l’Assistant, ainsi que les autorisations requises pour exécuter l’Assistant, consultez [exécuter le SQL Server Assistant Importation et exportation](start-the-sql-server-import-and-export-wizard.md).  
  
 La fonction de l'Assistant Importation et Exportation SQL Server est de copier des données d'une source vers une destination. L'Assistant peut également créer une base de données de destination et des tables de destination à votre intention. Toutefois, si vous devez copier plusieurs tables ou bases de données, ou autres types d'objets de bases de données, vous devez plutôt utiliser l'Assistant Copie de base de données. Pour plus d'informations, consultez [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Options  
 **Exécuter immédiatement**  
 Choisissez cette option pour lancer l'exécution du package immédiatement.  
  
 **Enregistrer le package SSIS**  
 Permet d'enregistrer le package pour une exécution ultérieure, avec la possibilité l'exécuter immédiatement.  
  
> [!NOTE]  
>  Dans [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], la possibilité d’enregistrer le package créé par l’Assistant n’est pas disponible.  
  
 **SQL Server**  
 Sélectionnez cette option pour enregistrer le package dans le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` base de données.  
  
> [!NOTE]  
>  Cette option est disponible uniquement si vous avez sélectionné le **enregistrer le Package SSIS** option.  
  
 **Système de fichiers**  
 Permet d'enregistrer le package en tant que fichier portant l'extension .dtsx.  
  
> [!NOTE]  
>  Cette option est disponible uniquement si vous avez sélectionné le **enregistrer le Package SSIS** option.  
  
 **Niveau de protection du package**  
 Sélectionnez un niveau de protection dans la liste.  
  
 Le niveau de protection détermine la méthode de protection (par mot de passe ou par clé utilisateur) et l'étendue de la protection du package. La protection peut inclure toutes les données ou uniquement les données sensibles. Pour comprendre les exigences et les options de sécurité de package, consultez [le contrôle d’accès pour les données sensibles dans des Packages](../security/access-control-for-sensitive-data-in-packages.md) et [vue d’ensemble de la sécurité &#40;Integration Services&#41;](../security/security-overview-integration-services.md).  
  
> [!NOTE]  
>  Cette option est disponible uniquement si vous avez sélectionné le **enregistrer le Package SSIS** option.  
  
 **Mot de passe**  
 Tapez un mot de passe.  
  
> [!NOTE]  
>  Cette option est disponible uniquement si vous avez défini le **au niveau de protection du Package** option **chiffrer les données sensibles avec un mot de passe** ou **chiffrer toutes les données avec un mot de passe**.  
  
 **Retapez le mot de passe**  
 Entrez à nouveau le mot de passe.  
  
> [!NOTE]  
>  Cette option est disponible uniquement si vous avez défini le **au niveau de protection du Package** option **chiffrer les données sensibles avec un mot de passe** ou **chiffrer toutes les données avec un mot de passe**.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de projets et de packages](../packages/run-integration-services-ssis-packages.md)   
 [Enregistrer des packages](../save-packages.md)  
  
  