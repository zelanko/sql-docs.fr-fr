---
title: Enregistrer et exécuter le package (Assistant importation et exportation SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.saveschedule.f1
ms.assetid: b582c462-3d7a-4a4c-a2a2-2c79fedab75a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2bb7f32cc36b14682de4629b238883acde4a015a
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85436816"
---
# <a name="save-and-execute-package-sql-server-import-and-export-wizard"></a>Enregistrer et exécuter le package (Assistant Importation et Exportation SQL Server)
  Utilisez la boîte de dialogue **enregistrer et exécuter le package** pour exécuter le package immédiatement, l’enregistrer pour l’exécuter ultérieurement, ou les deux.  
  
> [!NOTE]  
>   Si vous arrêtez un package avant la fin de son exécution, il n'est alors pas enregistré même si vous avez coché la case **Enregistrer** .  
  
 Pour en savoir plus sur cet Assistant, consultez [Assistant Importation et Exportation SQL Server](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Pour en savoir plus sur les options de démarrage de l’Assistant, ainsi que sur les autorisations requises pour exécuter correctement l’Assistant, consultez [exécuter l’Assistant importation et exportation SQL Server](start-the-sql-server-import-and-export-wizard.md).  
  
 La fonction de l'Assistant Importation et Exportation SQL Server est de copier des données d'une source vers une destination. L'Assistant peut également créer une base de données de destination et des tables de destination à votre intention. Toutefois, si vous devez copier plusieurs tables ou bases de données, ou autres types d'objets de bases de données, vous devez plutôt utiliser l'Assistant Copie de base de données. Pour plus d'informations, consultez [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Options  
 **Exécuter immédiatement**  
 Choisissez cette option pour lancer l'exécution du package immédiatement.  
  
 **Enregistrer le package SSIS**  
 Permet d'enregistrer le package pour une exécution ultérieure, avec la possibilité l'exécuter immédiatement.  
  
> [!NOTE]  
>  Dans [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], l'option permettant d'enregistrer le package créé par l'Assistant n'est pas disponible.  
  
 **SQL Server**  
 Sélectionnez cette option pour enregistrer le package dans la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` base de données.  
  
> [!NOTE]  
>  Cette option est disponible uniquement si vous avez sélectionné l’option **enregistrer le package SSIS** .  
  
 **Système de fichiers**  
 Permet d'enregistrer le package en tant que fichier portant l'extension .dtsx.  
  
> [!NOTE]  
>  Cette option est disponible uniquement si vous avez sélectionné l’option **enregistrer le package SSIS** .  
  
 **Niveau de protection du package**  
 Sélectionnez un niveau de protection dans la liste.  
  
 Le niveau de protection détermine la méthode de protection (par mot de passe ou par clé utilisateur) et l'étendue de la protection du package. La protection peut inclure toutes les données ou uniquement les données sensibles. Pour comprendre les exigences et les options de sécurité des packages, consultez [Access Control pour obtenir des données sensibles dans packages](../security/access-control-for-sensitive-data-in-packages.md) et [vue d’ensemble de la sécurité &#40;Integration Services&#41;](../security/security-overview-integration-services.md).  
  
> [!NOTE]  
>  Cette option est disponible uniquement si vous avez sélectionné l’option **enregistrer le package SSIS** .  
  
 **Mot de passe**  
 Tapez un mot de passe.  
  
> [!NOTE]  
>  Cette option est disponible uniquement si vous avez défini l’option **niveau de protection du package** pour **chiffrer les données sensibles avec un mot de passe** ou **chiffrer toutes les données avec le mot de passe**.  
  
 **Retapez le mot de passe**  
 Entrez à nouveau le mot de passe.  
  
> [!NOTE]  
>  Cette option est disponible uniquement si vous avez défini l’option **niveau de protection du package** pour **chiffrer les données sensibles avec un mot de passe** ou **chiffrer toutes les données avec le mot de passe**.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de projets et de packages](../packages/run-integration-services-ssis-packages.md)   
 [Enregistrer des packages](../save-packages.md)  
  
  
