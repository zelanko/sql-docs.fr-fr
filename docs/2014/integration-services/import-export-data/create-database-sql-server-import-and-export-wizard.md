---
title: Créer la base de données (Assistant Importation et Exportation SQL Server) | Microsoft Docs
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
- sql12.dts.impexpwizard.createdatabase.f1
ms.assetid: 56a8a79f-086c-4bdc-8888-0045bb4b0cbf
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: a2af52bdfbb4e6e2a2f5b069ff4555fbce7315bc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045183"
---
# <a name="create-database-sql-server-import-and-export-wizard"></a>Créer la base de données (Assistant Importation et Exportation SQL Server)
  Utilisez le **Create Database** page pour définir une nouvelle base de données pour un fichier de destination.  
  
 Cette page offre un sous-ensemble des options disponibles pour la création d'une base de données. Pour afficher toutes les options, utilisez [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Pour en savoir plus sur cet Assistant, consultez [SQL Server Assistant Importation et exportation](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Pour obtenir des informations sur les options de démarrage de l’Assistant, ainsi que sur les autorisations requises pour exécuter l’Assistant, consultez [exécuter le SQL Server Assistant Importation et exportation](start-the-sql-server-import-and-export-wizard.md).  
  
 La fonction de l'Assistant Importation et Exportation SQL Server est de copier des données d'une source vers une destination. L'Assistant peut également créer une base de données de destination et des tables de destination à votre intention. Toutefois, si vous devez copier plusieurs tables ou bases de données, ou autres types d'objets de bases de données, vous devez plutôt utiliser l'Assistant Copie de base de données. Pour plus d'informations, consultez [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Options  
 **Nom**  
 Fournissez un nom unique pour la base de données SQL Server de destination. Veillez à respecter les conventions SQL Server lorsque vous nommez la base de données.  
  
 **Nom de fichier de données**  
 Affiche le nom du fichier de données. Il est issu du nom de la base de données que vous avez fourni précédemment.  
  
 **Nom du fichier journal**  
 Affiche le nom du fichier journal. Il est issu du nom de la base de données que vous avez fourni précédemment.  
  
 **Taille initiale (fichier de données)**  
 Définissez le nombre de mégaoctets de la taille initiale du fichier de données.  
  
 **Aucune croissance autorisée (fichier de données)**  
 Indiquez si la taille du fichier de données peut augmenter au-delà de la taille initiale spécifiée.  
  
 **Augmenter de pourcentage (fichier de données)**  
 Définissez le pourcentage d'augmentation de la taille du fichier de données.  
  
 **Augmenter de taille (fichier de données)**  
 Définissez le nombre d'octets d'augmentation de la taille du fichier de données.  
  
 **Taille initiale (fichier journal)**  
 Définissez le nombre de mégaoctets de la taille initiale du fichier journal.  
  
 **Aucune croissance autorisée (fichier journal)**  
 Indiquez si la taille du fichier journal peut augmenter au-delà de la taille initiale spécifiée.  
  
 **Augmenter de pourcentage (fichier journal)**  
 Définissez le pourcentage d'augmentation du fichier journal.  
  
 **Augmenter de taille (fichier journal)**  
 Définissez le nombre d'octets d'augmentation de la taille du fichier journal.  
  
  