---
title: Lier des Applications Access vers SQL Server - base de données SQL Azure | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 08/17/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Access databases, linking to SQL Azure
- Access databases, linking to SQL Server
- auto-increment columns
- data types, unsupported
- hyperlink columns
- linking tables
- migrating databases, post-migration issues
- post-migration issues
- reference, post-migration issues
- refreshing linked tables
- slow performance
- unlinking tables
ms.assetid: 82374ad2-7737-4164-a489-13261ba393d4
caps.latest.revision: 19
author: Shamikg
ms.author: Shamikg
manager: murato
ms.openlocfilehash: 6a7dd2935bbd733621596c77fb5504a7ef552a96
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40395521"
---
# <a name="linking-access-applications-to-sql-server---azure-sql-db-accesstosql"></a>Liaison des applications Access vers SQL Server - Azure SQL DB (AccessToSQL)
Si vous souhaitez utiliser vos applications Access existantes avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez lier vos tables Access d’origine à migrées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou des tables de SQL Azure. La liaison modifie la base de données Access afin que vos pages d’accès aux requêtes, formulaires, rapports et données utilisent les données dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure au lieu des données dans votre base de données Access.  
  
> [!NOTE]  
> Votre accès aux tables restent dans Access, mais ne sont pas mis à jour avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou met à jour de SQL Azure. Une fois que vous liez les tables et vérifiez la fonctionnalité, vous souhaiterez peut-être supprimer votre accès aux tables.  
  
## <a name="linking-access-and-sql-server-tables"></a>Liaison des tables Access et SQL Server  
Lorsque vous liez une table Access vers un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou table SQL Azure, le moteur de base de données Jet stocke les informations de connexion et les métadonnées de table, mais les données sont stockées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure. Cette liaison permet à vos applications Access fonctionnent par rapport à l’accès aux tables, même si les tables réelles et les données sont dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure.  
  
> [!NOTE]  
> Si vous utilisez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification, votre mot de passe est stockée en texte clair sur l’accès aux tables liées. Nous vous recommandons d’utiliser l’authentification Windows.  
  
**Pour lier des tables**  
  
1.  Dans l’Explorateur de métadonnées d’accès, sélectionnez les tables que vous souhaitez lier.  
  
2.  Avec le bouton droit **Tables**, puis sélectionnez **lien**.  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) pour l’accès sauvegarde de la table d’accès d’origine et crée une table liée.  
  
Une fois que vous liez les tables, les tables de SSMA apparaissent avec une icône de lien petit. Dans Access, les tables apparaissent avec une icône « liée », qui est un globe avec une flèche pointant vers elle.  
  
Lorsque vous ouvrez une table dans Access, les données sont récupérées à l’aide d’un curseur keyset. Par conséquent, pour les tables volumineuses, toutes les les données ne sont récupérées en même temps. Toutefois, lorsque vous parcourez la table, accès récupère des données supplémentaires en fonction des besoins.  
  
> [!IMPORTANT]  
> Pour lier des tables access avec une base de données Azure, vous devez Client(SNAC) Native de SQL Server version 10.5 ou version ultérieure.   
> Vous pouvez obtenir la dernière version de SNAC de [Microsoft® SQL Server® 2008 R2 Feature Pack](http://go.microsoft.com/fwlink/?LinkId=196940).  
  
## <a name="unlinking-access-tables"></a>Dissociation accéder aux tables  
Lorsque vous supprimez le lien d’une table Access à partir d’un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou table SQL Azure, SSMA restaure la table d’accès d’origine et ses données.  
  
**Pour dissocier des tables**  
  
1.  Dans l’Explorateur de métadonnées d’accès, sélectionnez les tables que vous souhaitez dissocier.  
  
2.  Avec le bouton droit **Tables**, puis sélectionnez **dissocier**.  
  
## <a name="linking-tables-to-a-different-server"></a>Liaison des tables vers un autre serveur  
Si vous avez lié les tables de l’accès à une instance de SQL Server et que vous souhaitez ultérieurement modifier les liens vers une autre instance, vous devez relier les tables.  
  
**Pour lier des tables à un autre serveur**  
  
1.  Dans l’Explorateur de métadonnées d’accès, sélectionnez les tables que vous souhaitez dissocier.  
  
2.  Avec le bouton droit **Tables** , puis sélectionnez **dissocier**.  
  
3.  Cliquez sur le **reconnexion à SQL Server** bouton.  
  
4.  Connectez-vous à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure à laquelle vous souhaitez lier l’accès aux tables.  
  
5.  Dans l’Explorateur de métadonnées d’accès, sélectionnez les tables que vous souhaitez lier.  
  
6.  Avec le bouton droit **Tables**, puis sélectionnez **lien**.  
  
## <a name="updating-linked-tables"></a>La mise à jour des tables liées  
Si le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou définitions de table SQL Azure sont modifiées, vous pouvez supprimer le lien et puis reconnectez les tables de SSMA en procédant comme indiqué précédemment dans cette rubrique. Vous pouvez également mettre à jour les tables en utilisant l’accès.  
  
**Pour mettre à jour des tables liées à l’aide de l’accès**  
  
1.  Ouvrez la base de données Access.  
  
2.  Dans le **objets** , cliquez sur **Tables**.  
  
3.  Cliquez sur une table liée, puis sélectionnez **Gestionnaire d’attaches**.  
  
4.  Sélectionnez la case à cocher en regard de chaque table lié que vous souhaitez mettre à jour, puis cliquez sur **OK**.  
  
## <a name="possible-post-migration-issues"></a>Problèmes possibles de post-migration  
Les sections suivantes les problèmes de liste qui peuvent se produire dans les applications Access existantes après la migration des bases de données à partir de l’accès à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure, puis lier les tables, ainsi que les causes et les résolutions.  
  
### <a name="slow-performance-with-linked-tables"></a>Ralentissement des performances avec les tables liées  
**Cause :** certaines requêtes peuvent être lentes après la migration pour les raisons suivantes :  
  
-   L’application dépend des fonctions qui n’existent pas dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure, ce qui provoque Jet extraire des tables localement pour exécuter une requête SELECT.  
  
-   Requêtes qui mettre à jour ou supprimer le nombre de lignes sont renvoyées par Jet comme une requête paramétrable pour chaque ligne.  
  
**Résolution :** convertir les requêtes à exécution lente des requêtes pass-through, des procédures stockées ou des vues. Convertir les requêtes pass-through présente les problèmes suivants :  
  
-   Requêtes directes ne peut pas être modifiés. Modifier le résultat de la requête ou l’ajout de nouveaux enregistrements doit être effectuées dans une autre façon, comme par parler explicitement **modifier** ou **ajouter** boutons sur votre formulaire est lié à la requête.  
  
-   Certaines requêtes nécessitent l’entrée d’utilisateur, mais les requêtes pass-through ne prennent pas en charge l’entrée d’utilisateur. L’entrée d’utilisateur peut être obtenue en Visual Basic pour Applications (VBA) qui vous invite à entrer des paramètres, ou par un formulaire qui est utilisé comme un contrôle d’entrée. Dans les deux cas, le code VBA soumet la requête avec l’entrée utilisateur pour le serveur.  
  
### <a name="auto-increment-columns-are-not-updated-until-the-record-is-updated"></a>Colonnes à incrémentation automatique ne sont pas mis à jour jusqu'à ce que l’enregistrement est mis à jour  
**Cause :** après l’appel RecordSet.AddNew dans Jet, la colonne à incrémentation automatique est disponible avant l’enregistrement est mis à jour. Cela n’est pas vrai dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure. La nouvelle valeur de la valeur nouvelle colonne d’identité est disponible uniquement après l’enregistrement de l’enregistrement.  
  
**Résolution :** exécuter Visual Basic pour Applications (VBA) suivant avant d’accéder au champ d’identité :  
  
```  
Recordset.Update  
Recordset.Move 0,  
Recordset.LastModified  
```  
  
### <a name="new-records-are-not-available"></a>Nouveaux enregistrements ne sont pas disponibles  
**Cause :** lorsque vous ajoutez un enregistrement à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou une table SQL Azure à l’aide de VBA, si le champ de table index unique a une valeur par défaut et que vous n’affectez pas une valeur pour ce champ, le nouvel enregistrement n’apparaît pas jusqu'à ce que vous la rouvrirez dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou S SQL Azure. Si vous essayez d’obtenir une valeur à partir de l’enregistrement, le message d’erreur suivant s’affiche :  
  
`Run-time error '3167' Record is deleted.`  
  
**Résolution :** lorsque vous ouvrez le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure table à l’aide du code VBA, incluez la `dbSeeChanges` option, comme dans l’exemple suivant :  
  
`Set rs = db.OpenRecordset("TestTable", dbOpenDynaset, dbSeeChanges)`  
  
### <a name="after-migration-some-queries-will-not-allow-the-user-to-add-a-new-record"></a>Après la migration, certaines requêtes n’autorisera pas l’utilisateur d’ajouter un nouvel enregistrement  
**Cause :** si une requête n’inclut pas toutes les colonnes qui sont inclus dans un index unique, vous ne pouvez pas ajouter de nouvelles valeurs à l’aide de la requête.  
  
**Résolution :** vous assurer que toutes les colonnes incluses au moins un index unique font partie de la requête.  
  
### <a name="you-cannot-modify-a-linked-table-schema-with-access"></a>Vous ne pouvez pas modifier un schéma de table liée avec accès  
**Cause :** après la migration des données et la liaison des tables, l’utilisateur ne peut pas modifier le schéma d’une table dans Access.  
  
**Résolution :** modifier le schéma de table à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis mettez à jour le lien dans Access.  
  
### <a name="hyperlink-functionality-is-lost-after-migrating-data"></a>Lien hypertexte a cessé de fonctionner après la migration de données  
**Cause :** après la migration de données, des liens hypertexte dans les colonnes perdre leur fonctionnalité et deviennent simples **nvarchar (max)** colonnes.  
  
**Résolution :** None.  
  
### <a name="some-sql-server-data-types-are-not-supported-by-access"></a>Certains types de données SQL Server ne sont pas pris en charge par Access  
**Cause :** si vous mettez à jour ultérieurement votre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou des tables SQL Azure pour contenir des types de données qui ne sont pas pris en charge par l’accès, vous ne pouvez pas ouvrir la table dans Access.  
  
**Résolution :** vous pouvez définir une requête d’accès qui retourne uniquement les lignes avec des types de données pris en charge.  
  
## <a name="see-also"></a>Voir aussi  
[Migration bases de données Access vers SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
