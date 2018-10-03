---
title: Enregistrer le package SSIS (Assistant Importation et Exportation SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.savedtspackage.f1
ms.assetid: 7bf8ac6a-5599-43ab-bf5c-e072c11b85a0
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8b8ef62839d7379c35b55af7bcb65ab46e4b455d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048230"
---
# <a name="save-ssis-package-sql-server-import-and-export-wizard"></a>Enregistrer le package SSIS (Assistant Importation et Exportation SQL Server)
  Utilisez le **enregistrer le Package SSIS** page pour nommer, décrire et enregistrer un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Integration Services ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) du package pour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` de base de données ou à un fichier qui contient le .dtsx extension.  
  
> [!NOTE]  
>  Dans [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], la possibilité d’enregistrer le package créé par l’Assistant n’est pas disponible.  
  
 Pour en savoir plus sur cet Assistant, consultez [SQL Server Assistant Importation et exportation](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Pour en savoir plus sur les options de démarrage de l’Assistant et sur les autorisations requises pour exécuter l’Assistant avec succès, consultez [exécuter le SQL Server Assistant Importation et exportation](start-the-sql-server-import-and-export-wizard.md).  
  
 La fonction de l'Assistant Importation et Exportation SQL Server est de copier des données d'une source vers une destination. L'Assistant peut également créer une base de données de destination et des tables de destination à votre intention. Toutefois, si vous devez copier plusieurs tables ou bases de données, ou autres types d'objets de bases de données, vous devez plutôt utiliser l'Assistant Copie de base de données. Pour plus d'informations, consultez [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="static-options"></a>Options statiques  
 **Nom**  
 Permet de spécifier un nom unique pour le package.  
  
 **Description**  
 Permet de décrire le package. En règle générale, décrivez le package par rapport à sa fonction pour le rendre descriptif et faciliter sa gestion.  
  
 **Cible**  
 Afficher la cible ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou fichier) qui a été précédemment spécifié pour le fichier de destination.  
  
## <a name="target-dynamic-options"></a>Options dynamiques de la cible  
  
### <a name="target--sql-server"></a>Cible = SQL Server  
 **Nom du serveur**  
 Lorsque vous sélectionnez une destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], tapez ou sélectionnez le nom du serveur de destination.  
  
 **Utiliser l'authentification Windows**  
 Lorsque vous sélectionnez une destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], indiquez si la connexion au serveur utilise l'authentification intégrée Windows. Il s'agit de la méthode d'authentification conseillée.  
  
 **Utiliser l’authentification SQL Server**  
 Lorsque vous avez sélectionné un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, indiquez si vous souhaitez vous connecter au serveur à l’aide de l’authentification SQL Server.  
  
 **Nom d'utilisateur**  
 Lorsque vous avez sélectionné un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, et vous avez spécifié l’authentification de SQL Server, tapez le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nom d’utilisateur.  
  
 **Mot de passe**  
 Lorsque vous avez sélectionné un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, et vous avez spécifié l’authentification de SQL Server, tapez le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mot de passe.  
  
### <a name="target--file-system"></a>Cible = Système de fichiers  
 **Nom de fichier**  
 Lorsque vous avez sélectionné une destination de fichier, tapez le chemin d’accès du fichier de destination, ou utiliser le **Parcourir** bouton.  
  
 **Parcourir**  
 Lorsque vous avez sélectionné une destination de fichier, recherchez le fichier de destination à l’aide de la **enregistrer le Package** boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistrer des packages](../save-packages.md)  
  
  
