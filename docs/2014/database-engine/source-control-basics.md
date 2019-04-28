---
title: Présentation du contrôle de source | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- source controls [SQL Server Management Studio], providers
- source controls [SQL Server Management Studio]
- source controls [SQL Server Management Studio], about source controls
- source controls [SQL Server Management Studio], clients
ms.assetid: ca35b67a-104a-41fb-ac58-a61be06fe114
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bce3bd6862e612a8cefa35d1c981d608bf2c341c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62842983"
---
# <a name="source-control-basics"></a>Présentation du contrôle de code source
  Le contrôle de code source fait référence à un système dans lequel un logiciel serveur central stocke et effectue le suivi des versions de fichiers et contrôle l'accès aux fichiers. Un système de contrôle de code source comprend généralement un fournisseur de contrôle de code source et deux (voire plus) clients de contrôle de code source.  
  
## <a name="source-control-benefits"></a>Avantages présentés par le contrôle de code source  
 Lorsque vos fichiers sont gérés dans le cadre du contrôle de code source, vous êtes en mesure de  
  
-   Gérer le processus de transmission du contrôle des éléments d'une personne à une autre. Les fournisseurs de contrôle de code source prennent en charge l'accès à la fois partagé et exclusif à des fichiers. En cas d'accès exclusif aux fichiers projet, le fournisseur de contrôle de code source n'autorise qu'un seul utilisateur à la fois à extraire et à modifier ces fichiers. En cas d'accès partagé, plusieurs utilisateurs peuvent procéder à l'extraction de fichiers de script ; le fournisseur de contrôle de code source propose un dispositif de fusion des versions lors de leur archivage.  
  
-   Archiver des versions successives d'éléments sous contrôle de code source. Un fournisseur de contrôle de code source stocke les données qui permettent de distinguer une version d'un élément sous contrôle de code source d'une autre version. Le fournisseur stocke les différences entre les versions ainsi que des informations fondamentales sur la version : sa date de création, sa date de modification et l'auteur. Lorsque plusieurs personnes travaillent sur le même fichier, elles doivent utiliser la même page de codes afin que les versions puissent être comparées. Vous êtes ainsi en mesure de récupérer toute version d'un élément sous contrôle de code source. Vous pouvez également désigner toute version comme étant la dernière version de cet élément.  
  
-   Gérer des informations détaillées sur les historiques et les versions d'éléments sous contrôle de code source. Le contrôle de code source stocke la date et l'heure de la création de l'élément, de son extraction et de son archivage ainsi que le nom de l'utilisateur qui a réalisé l'action.  
  
-   Collaborer d'un projet à un autre. Grâce au partage de fichiers, plusieurs projets peuvent se partager des éléments sous contrôle de code source. Les modifications apportées à un élément partagé sont réfléchies dans tous les projets se partageant cet élément.  
  
-   Automatiser des opérations de contrôle de code source régulièrement effectuées. Un fournisseur de contrôle de code source peut définir une interface à partir de l'invite de commandes prenant en charge les principales fonctionnalités de contrôle de code source. Vous pouvez utiliser cette interface dans des fichiers de commandes par lot pour automatiser les tâches de contrôle de code source que vous effectuez régulièrement.  
  
-   Assurer une récupération en cas de suppressions accidentelles. Vous pouvez restaurer la dernière version de fichier archivée dans le contrôle de code source.  
  
-   Économiser de l'espace disque à la fois sur le serveur et sur le client du contrôle de code source. Certains fournisseurs de contrôle de code source, tels que [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe, prennent en charge l'économie d'espace disque sur le serveur en stockant la dernière version d'un fichier, les différences entre chaque version et la version qui la précède ou la suit. Visual SourceSafe prend en charge l'économie d'espace disque sur le client. Vous pouvez masquer des dossiers et des fichiers, de sorte qu'ils ne soient pas téléchargés sur votre disque local.  
  
 Les extractions de fichiers, les archivages et d'autres opérations de contrôle de code source sont en fait réalisées via un client de contrôle de code source tel que [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Le client est conçu pour dialoguer avec le fournisseur, de sorte que les fonctions du fournisseur soient disponibles auprès d'un groupe réparti d'utilisateurs. Grâce à un client de contrôle de code source, les utilisateurs peuvent parcourir les fichiers stockés par le fournisseur, ajouter et supprimer des fichiers, extraire et archiver des fichiers et récupérer des copies de fichiers locaux.  
  
> [!NOTE]  
>  Cette documentation implique que vous utilisiez [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe comme fournisseur de contrôle de code source. Si vous utilisez un autre fournisseur de contrôle de code source, vous devez distinguer des différences entre cette documentation et le logiciel que vous exécutez. Si vous constatez des différences, consultez la documentation pour connaître votre fournisseur de contrôle de code source.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|||  
|-|-|  
|**Tâche**|**Rubrique**|  
|Définir les options de contrôle de code Source|[Définir les options du contrôle de code source](../../2014/database-engine/set-source-control-options.md)|  
|Modifier le contrôle de code source connexions|[Modifier les connexions du contrôle de code source](../../2014/database-engine/change-source-control-connections.md)|  
|Exclure des fichiers de contrôle de code source|[Exclure des fichiers du contrôle de code source](../../2014/database-engine/exclude-files-from-source-control.md)|  
  
  
