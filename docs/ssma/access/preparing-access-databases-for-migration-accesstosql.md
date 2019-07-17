---
title: Préparation des bases de données Access pour la Migration (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 08/15/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Access databases, versions
- Access databases, when to migrate
- Access databases, workgroup security
- backing up databases
- documenting databases
- files, preparing
- migrating databases, versions
- migrating databases, when to migrate
- versions of Access
- workgroup security
ms.assetid: 9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114
author: Shamikg
ms.author: Shamikg
manager: murato
ms.openlocfilehash: 58988d31687cacdce2954d8e4098d509a9dcbb2b
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68260220"
---
# <a name="preparing-access-databases-for-migration-accesstosql"></a>Préparation des bases de données Access pour la migration (AccessToSQL)
Avant de migrer des bases de données Access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez déterminer les bases de données à migrer et vous assurer que ces bases de données sont prêtes pour la migration.  
  
## <a name="determining-when-to-migrate-to-sql-server"></a>Détermination des cas de migrer vers SQL Server  
Le moteur de base de données Jet, qui est utilisé en tant que le moteur de base de données pour l’accès, est une solution flexible et facile à utiliser pour la gestion des données. Toutefois, comme les bases de données deviennent plus volumineuses et plus stratégiques, de nombreux utilisateurs trouvent qu’elles nécessitent de meilleures performances, de sécurité ou de disponibilité. Pour les applications qui requièrent une plateforme de données plus robuste, envisagez de déplacer les bases de données sous-jacent pour les applications à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations sur le choix du moment auquel la migration, consultez le [page d’informations de migration](https://go.microsoft.com/fwlink/?LinkId=68571) sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] site Web.  
  
Après la migration des bases de données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez continuer à utiliser l’accès à l’aide de tables liées, ou vous pouvez migrer manuellement vos applications à [!INCLUDE[msCoName](../../includes/msconame_md.md)] code basé sur le .NET Framework qui interagit directement avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="determining-which-databases-to-migrate"></a>Déterminer les bases de données à migrer  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) pour l’accès puissent localiser des bases de données Access pour vous. Vous pouvez ensuite exporter les métadonnées relatives à ces bases de données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations sur l’exportation et d’interroger les métadonnées, consultez [exportation d’un inventaire Access](exporting-an-access-inventory-accesstosql.md).  

   > [!NOTE]
   > Pas toutes les fonctionnalités d’accès et les paramètres sont pris en charge par, ou peuvent être facilement converties en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Avant de commencer la migration des bases de données, consultez [fonctionnalités Access incompatibles](incompatible-access-features-accesstosql.md).
  
## <a name="preparing-for-migration"></a>Préparation pour la migration  
Utilisez les instructions suivantes pour aider à préparer vos bases de données Access pour la migration vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="upgrading-older-access-databases"></a>Mise à niveau les anciennes bases de données Access  
SSMA pour Access prend en charge Access 97 et versions ultérieures. Si vous avez des bases de données à partir de versions antérieures d’Access, ouvrir et enregistrer les bases de données dans Access 97 ou version ultérieure.  
  
### <a name="removing-workgroup-protection"></a>Suppression de la protection de groupe de travail  
SSMA ne peut pas migrer des bases de données qui utilisent la protection de groupe de travail. Pour supprimer la protection de groupe de travail à partir d’une base de données Access, procédez comme suit :  
  
1.  Copiez le fichier de base de données Access vers un autre emplacement.  
  
2.  Ouvrez la base de données copiée.  
  
3.  Sur le **outils** menu, pointez sur **sécurité**, puis sélectionnez **autorisations d’accès**.  
  
4.  Sélectionnez le **utilisateurs** option, sélectionnez le **administrateur** utilisateur, puis assurez-vous que le **administrer** cette autorisation est activée.  
  
5.  Sélectionnez le **groupes** option, sélectionnez le **utilisateurs** de groupe, puis assurez-vous que le **administrer** cette autorisation est activée.  
  
6.  Cliquez sur **OK**, puis, dans le **fichier** menu, cliquez sur **Exit**.  
  
Vous pouvez maintenant utiliser SSMA pour migrer la base de données copiée. Après avoir chargé le schéma dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez sécuriser manuellement la base de données sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="backing-up-databases"></a>Sauvegarde des bases de données  
Avant de migrer vos bases de données Access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez sauvegarder les accès aux bases de données que vous effectuez la migration, ainsi que les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans lequel vous allez migrer les bases de données accèdent aux objets et données.  
  
Pour sauvegarder une base de données Access, sur le **outils** menu, pointez sur **utilitaires de base de données**, puis sélectionnez **sauvegarder la base de données**.  
  
Pour plus d’informations sur la façon de sauvegarder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bases de données, consultez « sauvegarde et restauration des bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]» dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.  
  
### <a name="documenting-databases"></a>Documentation des bases de données  
Vous souhaiterez également les propriétés, telles que les listes d’objets de base de données, les tailles de fichier et les autorisations, vos bases de données d’accès de document. Pour générer cette documentation dans Access, sur le **outils** menu, pointez sur **analyser**, puis cliquez sur **documentées**.  
  
## <a name="see-also"></a>Voir aussi  
[Migration bases de données Access vers SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Liaison d’Applications Access vers SQL Server](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md)
