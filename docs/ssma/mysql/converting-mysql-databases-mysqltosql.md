---
title: Conversion de bases de données MySQL (MySQLToSQL) | Microsoft Docs
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
ms.assetid: ac21850b-fb32-4704-9985-5759b7c688c7
caps.latest.revision: 17
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 3ad0a909c9fce73955bee29070febfa32037a91c
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38985771"
---
# <a name="converting-mysql-databases-mysqltosql"></a>Conversion de bases de données MySQL (MySQLToSQL)
Après vous être connecté à MySQL, connecté à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou SQL Azure et définir le projet et les options de mappage de données, vous pouvez convertir des objets de base de données MySQL à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou objets de base de données SQL Azure.  
  
## <a name="the-conversion-process"></a>Le processus de Conversion  
Convertir des objets de base de données accepte les définitions d’objets à partir de MySQL, les convertit en similaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou SQL Azure objets et charge ensuite ces informations dans les métadonnées SSMA. Il ne charge pas les informations dans l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Vous pouvez ensuite afficher les objets et leurs propriétés à l’aide de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou de l’Explorateur de métadonnées SQL Azure.  
  
Lors de la conversion, SSMA imprime les messages de sortie dans le volet de sortie et messages d’erreur vers le volet Liste d’erreurs. Utilisez les informations de sortie et d’erreur pour déterminer si vous devez modifier vos bases de données MySQL ou votre processus de conversion pour obtenir les résultats de la conversion souhaitée.  
  
## <a name="setting-conversion-options"></a>Définition des Options de Conversion  
Avant de convertir des objets, passez en revue les options de conversion de projet dans le **paramètres du projet** boîte de dialogue. À l’aide de cette boîte de dialogue, vous pouvez définir comment SSMA convertit les tables et index. Pour plus d’informations, consultez [paramètres du projet &#40;Conversion&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-conversion-mysqltosql.md)  
  
## <a name="conversion-results"></a>Résultats de la conversion  
Le tableau suivant présente les objets de MySQL sont convertis et résultant [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] objets :  
  
|||  
|-|-|  
|**Objets de MySQL**|**Objets SQL Server qui en résulte**|  
|Tables avec des objets dépendants, tels que des index|SSMA crée des tables avec des objets dépendants. Table est convertie avec tous les index et contraintes. Les index sont convertis en distinct [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] objets.<br /><br />**Mappage de type de données spatiales** peut être effectuée uniquement au niveau de nœud de table.<br /><br />Pour plus d’informations sur les paramètres de Conversion de la Table, consultez [paramètres de Conversion](http://msdn.microsoft.com/f551cf6e-1575-4206-9cca-975b5b43a6b8)|  
|Fonctions|Si la fonction peut être directement convertie en données Transact-SQL, SSMA crée une fonction. Dans certains cas, la fonction doit être convertie à une procédure stockée. Cela est possible à l’aide de **fonction Conversion** dans Paramètres du projet. Dans ce cas, SSMA crée une procédure stockée et une fonction qui appelle la procédure stockée.<br /><br />**Choix donné :**<br /><br />Convertir en fonction des paramètres de projet<br /><br />Convertir (fonction)<br /><br />Conversion d’une procédure stockée<br /><br />Pour plus d’informations sur les paramètres de Conversion de la fonction, consultez [paramètres de Conversion](http://msdn.microsoft.com/f551cf6e-1575-4206-9cca-975b5b43a6b8)|  
|Procédures|Si la procédure peut être directement convertie en données Transact-SQL, SSMA crée une procédure stockée. Dans certains cas, une procédure stockée doit être appelée dans une transaction autonome. Dans ce cas, SSMA crée deux procédures stockées : celui qui implémente la procédure et une autre qui est utilisée pour appeler l’implémentation d’une procédure stockée.|  
|Conversion de la base de données|Bases de données en tant qu’objets de MySQL ne sont pas converties directement en SSMA pour MySQL. Bases de données MySQL sont traités plus comme un nom de schéma et tous les paramètres physiques sont perdues lors de la conversion. SSMA pour MySQL utilise [mappage de bases de données MySQL à des schémas de SQL Server &#40;MySQLToSQL&#41; ](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md) pour mapper des objets de base de données MySQL pour la paire de schéma/base de données SQL Server appropriée.|  
|Conversion de déclencheur|**SSMA crée des déclencheurs selon les règles suivantes :**<br /><br />AVANT la conversion des déclencheurs dans les déclencheurs INSTEAD OF T-SQL<br /><br />Déclencheurs AFTER sont convertis en déclencheurs après T-SQL avec ou sans itérations par lignes.|  
|Conversion de la vue|SSMA crée des vues avec des objets dépendants|  
|Conversion des instructions|-Chaque objet de l’instruction SQL peut contenir une seule instruction MySQL (telles que DDL, DML et autres types d’instructions) ou commencer... Bloc de fin.<br />-   **Conversion à instructions multiples : BEGIN... Conversion de bloc de fin**instruction SQL peut également contenir un BEGIN... Bloc de fin comme un dans la définition de procédure, fonction ou un déclencheur. Ces blocs doivent être converties de la même façon qu’ils sont convertis pour les objets d’instruction MySQL uniques.|  
  
## <a name="converting-mysql-database-objects"></a>Convertir des objets de base de données MySQL  
Pour convertir des objets de base de données MySQL, vous sélectionnez d’abord les objets que vous souhaitez convertir, puis SSMA effectuer la conversion. Pour afficher les messages de sortie pendant la conversion, sur le **vue** menu, sélectionnez **sortie**.  
  
**Pour convertir des objets de MySQL à la syntaxe SQL Server ou SQL Azure**  
  
1.  Dans l’Explorateur de métadonnées de MySQL, développez le serveur MySQL, puis puis **bases de données**.  
  
2.  Sélectionnez les objets à convertir :  
  
    -   Pour convertir tous les schémas, sélectionnez la case à cocher à côté **bases de données**.  
  
    -   Pour convertir ou omettre une base de données, sélectionnez la case à cocher en regard du nom de la base de données.  
  
    -   Pour convertir ou omettre une catégorie d’objets, développez un schéma, puis sélectionnez ou désactivez la case à cocher en regard de la catégorie.  
  
    -   Pour convertir ou omettre des objets, développez le dossier de catégorie, puis sélectionnez ou désactivez la case à cocher en regard de l’objet.  
  
3.  Pour convertir tous les objets sélectionnés, cliquez sur **bases de données** et sélectionnez **convertir le schéma**.  
  
    Vous pouvez également convertir des objets individuels ou des catégories d’objets en double-cliquant sur l’objet ou son dossier parent, puis en sélectionnant **convertir le schéma**.  
  
## <a name="viewing-conversion-problems"></a>Affichage des problèmes de Conversion  
Certains objets MySQL ne peuvent pas être converties. Vous pouvez déterminer le taux de réussite de la conversion en affichant le rapport de synthèse de conversion.  
  
**Pour afficher un rapport de synthèse**  
  
1.  Dans l’Explorateur de métadonnées de MySQL, sélectionnez **bases de données**.  
  
2.  Dans le volet droit, sélectionnez le **rapport** onglet.  
  
    Ce rapport affiche le rapport d’évaluation de résumé pour tous les objets de base de données qui ont été évaluées ou converti. Vous pouvez également afficher un rapport de synthèse pour des objets individuels :  
  
    -   Pour afficher le rapport pour un schéma individuel, sélectionnez la base de données dans l’Explorateur de métadonnées de MySQL.  
  
    -   Pour afficher le rapport pour un objet individuel, sélectionnez l’objet dans l’Explorateur de métadonnées de MySQL. Les objets qui présentent des problèmes de conversion ont une icône d’erreur rouge.  
  
Pour les objets en échec de conversion, vous pouvez afficher la syntaxe qui a entraîné l’échec de conversion.  
  
**Pour afficher les problèmes de conversion individuels**  
  
1.  Dans l’Explorateur de métadonnées de MySQL, développez **bases de données**.  
  
2.  Développez la base de données qui affiche une icône d’erreur rouge.  
  
3.  Sous la base de données, développez un dossier qui a une icône d’erreur rouge.  
  
4.  Sélectionnez l’objet qui a une icône d’erreur rouge.  
  
5.  Dans le volet droit, cliquez sur le **rapport** onglet.  
  
6.  En haut de la **rapport** onglet est une liste déroulante. Si la liste affiche **statistiques**, modifiez la sélection à **Source**.  
  
    SSMA affichera le code source et plusieurs boutons immédiatement au-dessus du code.  
  
7.  Cliquez sur le **problème suivant** bouton. Il s’agit d’une icône d’erreur rouge avec une flèche qui pointe vers la droite.  
  
    SSMA met en évidence le premier code source problématiques qu’il trouve dans l’objet actuel.  
  
Pour chaque élément qui ne peut pas être converti, vous devez déterminer ce que vous voulez faire avec cet objet :  
  
-   Vous pouvez modifier l’objet dans la base de données MySQL pour supprimer ou de réviser le code problématique. Pour charger le code mis à jour dans SSMA, vous devrez mettre à jour les métadonnées. Pour plus d’informations, consultez [connexion à MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
-   Vous pouvez exclure l’objet de la migration. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou de l’Explorateur de métadonnées SQL Azure et l’Explorateur de métadonnées de MySQL, désactivez la case à cocher en regard de l’élément avant de charger les objets vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou SQL Azure et la migration des données à partir de MySQL.  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante du processus de migration est [le chargement des objets de base de données convertis dans SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/loading-converted-database-objects-into-sql-server-mysqltosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Bases de données de migration de MySQL vers SQL Server - Azure SQL DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
