---
title: Fonctionnalités Access incompatibles (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Access databases
- Access databases, features incompatible with SQL Azure
- Access databases, features incompatible with SQL Server
- dates
- default expressions
- foreign keys
- hyperlink columns
- incompatible Access features
- indexes
- indexes, length of
- keywords
- primary keys
- reference, incompatible features
- replication columns
- special characters
- unique indexes
- validation rules
ms.assetid: 99d45b9c-e3b9-4d56-8c25-b594b887ace1
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 29b5225f95c6b2cb04f42c0e67c504ac2cb20e53
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62740896"
---
# <a name="incompatible-access-features-accesstosql"></a>Fonctionnalités Access incompatibles (AccessToSQL)
Pas toutes les fonctionnalités de base de données Access sont compatibles avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par exemple, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et accès avoir différents jeux de mots clés réservés. Considérations de ceux-ci peuvent empêcher une migration réussie vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Utilisez le tableau suivant pour en savoir plus sur les problèmes de migration possible et ce que vous pouvez faire à leur sujet.  
  
## <a name="database-settings-or-features-that-might-affect-migration"></a>Paramètres de base de données ou des fonctionnalités qui peuvent affecter la Migration  
  
|Paramètre de base de données ou une fonctionnalité d’accès|Problème de migration|  
|--------------------------------------|-------------------|  
|Accéder aux tables n’ont pas d’index uniques.|Si une table qui n’a pas un index unique est migrée vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous ne pouvez pas modifier la table après la migration. Cela peut entraîner des problèmes de compatibilité des applications.<br /><br />Lorsque vous convertissez des objets de base de données Access, la fenêtre Sortie affiche tout accès aux tables qui n’ont pas d’index uniques.<br /><br />Vous pouvez configurer l’accès pour ajouter une clé primaire sur la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table lors de la conversion. Pour plus d’informations, consultez [paramètres du projet (Conversion)](https://msdn.microsoft.com/bcebc635-c638-4ddb-924c-b9ccfef86388).|  
|Accès aux tables ont des colonnes de la réplication.|Si une table Access qui inclut les colonnes système de réplication est migrée vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la fonctionnalité de réplication Jet sera rompue après la migration.<br /><br />Après la migration, envisagez d’utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] réplication pour maintenir les copies synchronisées de vos bases de données.|  
|Accès aux tables qui ont des index uniques contiennent plusieurs valeurs null.|Accès aux tables qui ont des index uniques avec plusieurs valeurs null ne peut pas être transféré à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], car dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], index uniques ne pas autoriser plusieurs valeurs NULL. Migration échoue pour ces tables.<br /><br />SSMA marquera ce problème dans les rapports d’évaluation. Pour créer un rapport d’évaluation, consultez [évaluation des objets de base de données Access pour la Conversion](assessing-access-database-objects-for-conversion-accesstosql.md).<br /><br />Si ce problème se produit, il se peut que vous devez vous assurer que la clé primaire n’a pas de valeurs null en double. Ou bien, vous devez supprimer la clé primaire ou index uniques qui contiennent plusieurs valeurs null.|  
|Accès aux tables contiennent des valeurs de date qui sont hors de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] plage.|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime** type accepte les dates dans la plage du 1 janvier 1753 au 31 décembre 9999 uniquement. Accès accepte les dates dans la plage de 1 100 janvier au 31 décembre 9999.<br /><br />SSMA marquera ce problème dans les rapports d’évaluation. Pour créer un rapport d’évaluation, consultez [évaluation des objets de base de données Access pour la Conversion](assessing-access-database-objects-for-conversion-accesstosql.md).<br /><br />Vous pouvez configurer la manière dont SSMA résout les dates qui sont hors de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] plage. Pour plus d’informations, consultez [paramètres du projet (Migration)](https://msdn.microsoft.com/4caebc9c-8680-4b99-a8fa-89c43161c95d).|  
|Index des longueurs dans Access dépassent 900 octets.|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les index ont une limite de 900 octets pour la taille totale des colonnes clés d’index. Si votre accès aux tables utilisation d’index plus grands, SSMA affiche un avertissement.<br /><br />Si vous poursuivez la migration des données, la migration peut échouer.|  
|Accès aux noms d’objet sont [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mots clés, ou contenir des caractères spéciaux.|Accès et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avoir différents jeux de mots clés réservés et caractères spéciaux. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accepte les objets sont nommés à l’aide de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mots clés ou qui contiennent des caractères spéciaux de si vous utilisez des identificateurs entre crochets ou entre guillemets, par exemple, « select » ou [] .p. Pour plus d’informations, consultez « Identificateurs délimité (moteur de base de données) » dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.<br /><br />**REMARQUE :** Pour utiliser des guillemets pour délimiter des identificateurs, SET QUOTED_IDENTIFIER doit être ON.<br /><br />Par exemple, `CREATE TABLE [schema](c1 [FOR])` est une instruction valide, même si **schéma** et **pour** sont des mots clés réservés. En outre, `CREATE TABLE [xxx*yyy](c1 x&y)` est une instruction valide, même si le nom de table et de colonne contenir les caractères spéciaux  **\&#42 ;** et **&amp;** .<br /><br />Toutes les requêtes qui font référence à ces objets doivent également utiliser les noms avec crochets ou guillemets. Par exemple, la requête `SELECT * FROM schema` échouera. La requête correcte est : `SELECT * FROM [schema]`.<br /><br />Lorsque vous convertissez des objets de base de données Access, le volet de sortie répertorie toutes les tables Access qui utilisent des mots clés ou des caractères spéciaux. Vous pouvez modifier les tables dans Access, puis supprimez et rajoutez la base de données ; ou vous pouvez modifier les requêtes qui font référence à ces objets afin que les requêtes utilisent des crochets ou guillemets pour délimiter des identificateurs. Si vous ne modifiez pas vos requêtes, vos applications Access peuvent renvoyer des erreurs ou d’autres problèmes.|  
|Tailles de champ diffèrent dans les relations clé primaire/étrangère clées.|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge la fonctionnalité de Jet de la liaison des colonnes qui ont différents types de données ou tailles avec des contraintes de clé étrangères.<br /><br />Lorsque vous convertissez des objets de base de données Access, la fenêtre Sortie affiche des contraintes de clé étrangère/clé primaires qui ne seront pas converties en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez modifier les types de données et tailles sur les colonnes de l’accès afin qu’ils correspondent, puis supprimez et rajoutez la base de données Access. Ou, vous pouvez migrer les données même si ces contraintes ne seront pas créées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|Les tables référencées dans les relations d’accès ont une clé primaire, ni un index unique.|Accès accepte la relation entre les tables où la table référencée n’a pas une clé primaire ou un index unique. Toutefois, cela ne prend pas en charge [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br />Lorsque vous convertissez des objets de base de données Access, la fenêtre Sortie affiche toutes les tables qui n’ont des relations, mais aucune clé primaire ou un index unique. Vous pouvez modifier les tables pour ajouter des clés primaires ou des index uniques, puis supprimez et rajoutez la base de données Access. Ou bien, vous pouvez migrer les données même si la relation entre les tables sera rompue.|  
|Accès aux tables ont des colonnes de lien hypertexte.|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge **hyperlink** colonnes. Au lieu de cela, les colonnes sont traitées comme des colonnes d’avoir accès. Par défaut, ces colonnes seront convertis en **nvarchar (max)** colonnes dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez personnaliser le mappage. Pour plus d’informations, consultez [Source de mappage et les Types de données cible](mapping-source-and-target-data-types-accesstosql.md).|  
|Expressions de règle de validation ou la valeur par défaut contiennent des fonctions d’accès qui ne peut pas être converties en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure.|Expressions d’accès par défaut ou les règles de validation peuvent inclure des fonctions d’accès au système ou des fonctions définies par l’utilisateur qui ne correspondent pas à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure. À l’aide de fonctions qui ne correspondent pas aux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure vous empêche de charger les expressions par défaut ou les règles de validation dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure.|  
  
## <a name="see-also"></a>Voir aussi  
[Préparation des bases de données Access pour la Migration](preparing-access-databases-for-migration-accesstosql.md)  
[Migration bases de données Access vers SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
