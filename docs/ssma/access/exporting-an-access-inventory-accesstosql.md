---
title: Exportation d’un inventaire Access (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Access databases
- Access databases, exporting metadata
- exporting
- exporting Access metadata
- exporting, Access metadata
- exporting, querying exported metadata
- inventories of Access databases
- querying exported metadata
ms.assetid: 7e1941fb-3d14-4265-aff6-c77a4026d0ed
caps.latest.revision: 18
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 6256a21e699f3dbd6714da0e4778b9d00e8d940a
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40394660"
---
# <a name="exporting-an-access-inventory-accesstosql"></a>Exportation d’un inventaire Access (AccessToSQL)
Si vous avez plusieurs bases de données Access et que vous ne savez pas lesquels pour migrer vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez exporter un inventaire de toutes les bases de données Access dans un projet. Vous pouvez ensuite consulter et interroger les métadonnées d’inventaire pour déterminer les bases de données et les objets au sein de ces bases de données à migrer. Cet inventaire vous permet de rapidement trouver les réponses aux questions, telles que les éléments suivants :  
  
-   Quelles sont les plus grandes bases de données ?  
  
-   Propriétaire de la plupart des bases de données ?  
  
-   Les bases de données contiennent les mêmes tables ?  
  
-   Les bases de données n’ont pas été modifiés au cours des six derniers mois ?  
  
-   Les bases de données contiennent des informations privées ?  
  
Exemples de requêtes qui sont utilisés pour répondre à ces questions sont fournis à la fin de cette rubrique.  
  
## <a name="exported-metadata"></a>Métadonnées exportées  
SSMA exporte les métadonnées relatives à accès bases de données, tables, colonnes, index, clés étrangères, requêtes, rapports, formulaires, macros et modules. Métadonnées relatives à chacune de ces catégories d’éléments sont exportée vers une table distincte. Pour les schémas de ces tables, consultez [schémas d’inventaire Access](access-inventory-schemas-accesstosql.md).  
  
## <a name="exporting-inventory-data"></a>Exportation des données d’inventaire  
Pour exporter un inventaire de l’accès, vous devez tout d’abord ouvrir ou créer un projet SSMA et puis ajoutez la base de données Access que vous souhaitez analyser. Après avoir ajouté des bases de données à un projet SSMA, exporter des métadonnées relatives à ces bases de données à une certaine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données et le schéma. Si nécessaire, SSMA crée des tables pour stocker les métadonnées. SSMA puis ajoute les métadonnées concernant les bases de données Access à le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données.  
  
> [!NOTE]  
> Une base de données Access peut être fractionnée en plusieurs fichiers : une base de données principale qui contient des tables et des bases de données frontales qui contiennent des requêtes, formulaires, rapports, macros, modules et raccourcis. Si vous souhaitez migrer une base de données fractionnement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ajouter la base de données frontale SSMA.  
  
Les instructions suivantes décrivent comment créer un projet, ajouter des bases de données au projet, vous connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], puis exporter les données d’inventaire.  
  
**Pour créer un projet**  
  
1.  Ouvrez SSMA pour Access.  
  
2.  Dans le menu **Fichier**, sélectionnez **Nouveau projet**.  
  
    La boîte de dialogue **Nouveau projet** s'affiche.  
  
3.  Dans la zone **Nom** , tapez le nom de votre projet.  
  
4.  Dans le **emplacement** zone, entrez ou sélectionnez un dossier pour le projet.  
  
5.  Dans le **migrer vers** liste déroulante, sélectionnez la version cible auquel vous souhaitez migrer, puis cliquez sur **OK**.  
  
Pour plus d’informations sur la création de projets, consultez [Creating and Managing Projects](creating-and-managing-projects-accesstosql.md).  
  
**Pour rechercher et ajouter des bases de données**  
  
1.  Sur le **fichier** menu, cliquez sur **trouver les bases de données**.  
  
2.  Dans l’Assistant trouver les bases de données, entrez le lecteur, chemin d’accès de fichier ou le chemin d’accès UNC que vous souhaitez rechercher. Sinon, cliquez sur **Parcourir** pour sélectionner le dossier de disque ou réseau.  
  
3.  Cliquez sur **ajouter** pour ajouter l’emplacement à la zone de liste.  
  
    Répétez les deux étapes précédentes pour ajouter des emplacements de recherche supplémentaires.  
  
4.  Si vous le souhaitez, ajouter des critères de recherche pour affiner la liste des bases de données qui sont retournées.  
  
    > [!IMPORTANT]  
    > Le **tout ou partie du nom de fichier** zone de texte ne prend pas en charge les caractères génériques.  
  
5.  Cliquez sur **analyse**.  
  
    La page d’analyse s’affiche. Elle indique les bases de données qui ont été trouvés et la progression de la recherche. Pour arrêter la recherche, cliquez sur **arrêter**.  
  
6.  Dans la page Sélectionner les fichiers, sélectionnez chaque base de données que vous souhaitez ajouter au projet.  
  
    Vous pouvez utiliser la **sélectionner tout** et **Effacer tout** boutons en haut de la liste pour sélectionner ou effacer toutes les bases de données. Vous pouvez également maintenez la touche CTRL enfoncée pour sélectionner plusieurs lignes, ou maintenez la touche MAJ ENFONCÉE pour sélectionner une plage de lignes.  
  
7.  Cliquez sur **Suivant**.  
  
8.  Dans la page vérifier, cliquez sur **Terminer**.  
  
Pour plus d’informations sur l’ajout de bases de données à des projets, consultez [Ajout et suppression des fichiers de base de données Access](adding-and-removing-access-database-files-accesstosql.md).  
  
**Pour vous connecter à SQL Server**  
  
1.  Sur le **fichier** menu, sélectionnez **se connecter à SQL Server**.  
  
2.  Dans la boîte de dialogue de connexion, entrez ou sélectionnez le nom de l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Si vous vous connectez à l’instance par défaut sur l’ordinateur local, vous pouvez entrer **localhost** ou un point (**.**).  
  
    -   Si vous vous connectez à l’instance par défaut sur un autre ordinateur, entrez le nom de l’ordinateur.  
  
    -   Si vous vous connectez à une instance nommée, entrez le nom d’ordinateur, une barre oblique inverse et le nom d’instance. Par exemple : MyServer\MyInstance.  
  
3.  Dans le **base de données** , entrez le nom de la base de données cible pour les métadonnées exportées.  
  
4.  Si votre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré pour accepter les connexions sur un port non défini par défaut, entrez le numéro de port qui est utilisé pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexions dans le **port du serveur** boîte. L’instance par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le numéro de port par défaut est 1433. Pour les instances nommées, SSMA tente d’obtenir le numéro de port à partir de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Browser.  
  
5.  Dans le **authentification** menu déroulant, sélectionnez type d’authentification à utiliser pour la connexion. Pour utiliser le compte Windows actuel, sélectionnez **l’authentification Windows**. Pour utiliser un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion, sélectionnez **l’authentification SQL Server**, puis indiquez un nom d’utilisateur et le mot de passe.  
  
Pour plus d’informations sur la connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [connexion à SQL Server &#40;AccessToSQL&#41;](../../ssma/access/connecting-to-sql-server-accesstosql.md).  
  
**Pour exporter les informations d’inventaire**  
  
1.  Dans l’Explorateur de métadonnées d’accès, développez **la métabase accès**.  
  
2.  Activez la case à cocher **bases de données**.  
  
    Pour omettre les bases de données individuelles ou des objets de base de données, développez le **bases de données** dossier et désactivez la case à cocher en regard de la base de données ou l’objet de base de données.  
  
3.  Avec le bouton droit **bases de données** et sélectionnez **exporter le schéma**.  
  
4.  Dans le **sélectionner le schéma pour l’exportation** boîte de dialogue, sélectionnez le schéma cible pour les métadonnées exportées, puis cliquez sur **OK**.  
  
Chaque fois que vous exportez des métadonnées, SSMA ajoute les données à l’inventaire. Les données existantes dans l’inventaire ne sont pas mis à jour ou supprimées.  
  
## <a name="querying-the-exported-metadata"></a>Interrogation des métadonnées exportées  
Après avoir exporté les métadonnées sur les bases de données Access, vous pouvez interroger les métadonnées. Les instructions suivantes expliquent comment pour utiliser la fenêtre Éditeur de requête dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour exécuter des requêtes.  
  
**Pour interroger les métadonnées**  
  
1.  À partir de la **Démarrer** menu, pointez sur **tous les programmes**, pointez sur **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005** ou **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008**ou **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012**, puis cliquez sur **SQL Server Management Studio**.  
  
2.  Dans le **se connecter au serveur** boîte de dialogue, vérifiez les paramètres, puis cliquez sur **Connect**.  
  
3.  Dans la barre d’outils de Management Studio, cliquez sur **nouvelle requête** pour ouvrir l’éditeur de requête.  
  
4.  Dans la fenêtre Éditeur de requête, entrez une requête. Certains exemples sont présentés dans la section suivante.  
  
5.  Appuyez sur la touche F5 pour exécuter la requête.  
  
## <a name="query-examples"></a>Exemples de requêtes  
Avant d’exécuter une des requêtes suivantes, vous devez exécuter une utilisation *database_name* requête s’assurer que les requêtes sont exécutées sur la base de données qui contient les métadonnées exportées. Par exemple, si vous avez exporté les métadonnées pour une base de données nommé MyAccessMetadata, ajoutez ce qui suit au début de la [!INCLUDE[tsql](../../includes/tsql-md.md)] code :  
  
```  
USE MyAccessMetadata;  
GO  
```  
Les exemples ci-après utilisent tous le **dbo** schéma. Si vous avez exporté les métadonnées vers un autre schéma, veillez à modifier le schéma lorsque vous exécutez ces requêtes.  
  
### <a name="what-tables-and-columns-are-in-these-databases"></a>Quelles tables et colonnes sont dans ces bases de données ?  
La requête suivante joint les tables qui contiennent les métadonnées de la base de données, de table et de colonne, puis retourne les noms de toutes les bases de données, tables et colonnes, triés par nom de colonne :  
  
```  
SELECT DatabaseName, TableName, ColumnName   
FROM dbo.SSMA_Access_InventoryColumns C  
JOIN dbo.SSMA_Access_InventoryTables T  
ON C.TableId = T.TableId  
JOIN dbo.SSMA_Access_InventoryDatabases D  
ON T.DatabaseId = D.DatabaseId  
ORDER BY ColumnName;  
```  
  
### <a name="what-are-the-largest-databases"></a>Quelles sont les plus grandes bases de données ?  
La requête suivante retourne le nom de la base de données, la taille du fichier et le nombre de tables dans chaque base de données Access, trié par taille de fichier :  
  
```  
SELECT DatabaseName, FileSize, TablesCount  
FROM dbo.SSMA_Access_InventoryDatabases  
ORDER BY FileSize DESC;  
```  
  
### <a name="who-is-the-owner-of-most-of-the-databases"></a>Qui est le propriétaire de la plupart des bases de données ?  
La requête suivante retourne le nom de la base de données et le propriétaire de chaque base de données Access, trié par propriétaire.  
  
```  
SELECT DatabaseName, FileOwner  
FROM dbo.SSMA_Access_InventoryDatabases  
ORDER BY FileOwner;  
```  
  
### <a name="which-databases-contain-the-same-tables"></a>Les bases de données contiennent les mêmes tables ?  
La requête suivante utilise une sous-requête pour rechercher tous les noms de table qui apparaissent plusieurs fois dans la liste des tables et utilise ensuite cette liste de tables pour obtenir le nom de la base de données. Les résultats sont retournés en tant que le nom de la base de données, puis le nom de table et sont triés par nom de la table.  
  
```  
SELECT DatabaseName, TableName   
FROM dbo.SSMA_Access_InventoryTables T  
JOIN dbo.SSMA_Access_InventoryDatabases D  
ON D.DatabaseId = T.DatabaseId  
WHERE TableName IN (  
SELECT TableName   
FROM dbo.SSMA_Access_InventoryTables  
GROUP BY TableName   
HAVING count(*)>1  
)  
ORDER BY TableName;  
```  
  
### <a name="which-databases-were-not-modified-in-the-last-six-months"></a>Les bases de données n’ont pas été modifiés au cours des six derniers mois ?  
La requête suivante obtient la date actuelle, obtient la valeur de mois pendant six mois il y a et renvoie une liste de bases de données avec une date de modification de plus de six mois auparavant.  
  
```  
SELECT DatabaseName, DateModified  
FROM dbo.SSMA_Access_InventoryDatabases  
WHERE DATEDIFF(month, DateModified, GETDATE()) > 6  
ORDER BY DateModified;  
```  
  
### <a name="which-databases-contain-private-information"></a>Les bases de données contiennent des informations privées ?  
Vos bases de données Access peuvent contenir des informations sensibles ou personnelles. Vous souhaiterez peut-être déplacer ces bases de données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour tirer parti de ses fonctionnalités de sécurité. Si vous savez que les colonnes contenant des données sensibles ont un nom spécifique, ou contiennent des caractères spécifiques, vous pouvez utiliser une requête pour rechercher toutes les colonnes qui contiennent ces informations. Par exemple, vous trouverez toutes les colonnes qui contiennent la chaîne « salaire ».  La requête retourne ensuite le nom de la base de données, le nom de la table et le nom de colonne.  
  
```  
SELECT DatabaseName, TableName, ColumnName   
FROM dbo.SSMA_Access_InventoryColumns C  
JOIN dbo.SSMA_Access_InventoryTables T  
ON C.TableId = T.TableId  
JOIN dbo.SSMA_Access_InventoryDatabases D  
ON T.DatabaseId = D. DatabaseId  
WHERE ColumnName LIKE '%salary%';  
```  
Si vous ne connaissez pas le nom de colonne, vous pouvez écrire une requête pour retourner toutes les colonnes. Pour ce faire, supprimez la clause WHERE de la requête précédente.  
  
## <a name="see-also"></a>Voir aussi  
[Préparation des bases de données Access pour la Migration](preparing-access-databases-for-migration-accesstosql.md)  
  
