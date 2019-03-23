---
title: Enregistrer le package SSIS (Assistant Importation et Exportation SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.savedtspackage.f1
ms.assetid: 7bf8ac6a-5599-43ab-bf5c-e072c11b85a0
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 6af26cafd4f8dd9bf874ae7860c4f796bef48ae1
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58387273"
---
# <a name="save-ssis-package-sql-server-import-and-export-wizard"></a>Enregistrer le package SSIS (Assistant Importation et Exportation SQL Server)
  Utilisez le **enregistrer le Package SSIS** page pour nommer, décrire et enregistrer un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Integration Services ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) du package pour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` de base de données ou à un fichier qui contient le .dtsx extension.  
  
> [!NOTE]  
>  Dans [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], l'option permettant d'enregistrer le package créé par l'Assistant n'est pas disponible.  
  
 Pour en savoir plus sur cet Assistant, consultez [Assistant Importation et Exportation SQL Server](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Pour en savoir plus sur les options de démarrage de l’Assistant et sur les autorisations requises pour exécuter l’Assistant avec succès, consultez [exécuter le SQL Server Assistant Importation et exportation](start-the-sql-server-import-and-export-wizard.md).  
  
 La fonction de l'Assistant Importation et Exportation SQL Server est de copier des données d'une source vers une destination. L'Assistant peut également créer une base de données de destination et des tables de destination à votre intention. Toutefois, si vous devez copier plusieurs tables ou bases de données, ou autres types d'objets de bases de données, vous devez plutôt utiliser l'Assistant Copie de base de données. Pour plus d'informations, consultez [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="static-options"></a>Options statiques  
 **Nom**  
 Permet de spécifier un nom unique pour le package.  
  
 **Description**  
 Permet de décrire le package. En règle générale, décrivez le package par rapport à sa fonction pour le rendre descriptif et faciliter sa gestion.  
  
 **Cible**  
 Permet d'afficher la cible ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou fichier) définie préalablement pour le fichier de destination.  
  
## <a name="target-dynamic-options"></a>Options dynamiques de la cible  
  
### <a name="target--sql-server"></a>Cible = SQL Server  
 **Nom du serveur**  
 Lorsque vous sélectionnez une destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], tapez ou sélectionnez le nom du serveur de destination.  
  
 **Utiliser l'authentification Windows**  
 Lorsque vous sélectionnez une destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], indiquez si la connexion au serveur utilise l'authentification intégrée Windows. Il s'agit de la méthode d'authentification conseillée.  
  
 **Utiliser l’authentification SQL Server**  
 Lorsque vous sélectionnez une destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], indiquez si la connexion au serveur utilise l'authentification SQL Server.  
  
 **Nom d'utilisateur**  
 Lorsque vous sélectionnez une destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et définissez l'authentification SQL Server, tapez le nom d'utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Mot de passe**  
 Lorsque vous sélectionnez une destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et définissez l'authentification SQL Server, tapez le mot de passe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="target--file-system"></a>Cible = Système de fichiers  
 **Nom de fichier**  
 Lorsque vous avez sélectionné une destination de fichier, tapez le chemin d’accès du fichier de destination, ou utiliser le **Parcourir** bouton.  
  
 **Parcourir**  
 Lorsque vous avez sélectionné une destination de fichier, recherchez le fichier de destination à l’aide de la **enregistrer le Package** boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistrer des packages](../save-packages.md)  
  
  
