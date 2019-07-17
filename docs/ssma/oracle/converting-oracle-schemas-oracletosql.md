---
title: Conversion de schémas Oracle (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Conversion Results
ms.assetid: e021182d-31da-443d-b110-937f5db27272
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 638c16de8312456410c14e38fa632085e504913e
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68266150"
---
# <a name="converting-oracle-schemas-oracletosql"></a>Conversion de schémas Oracle (OracleToSQL)
Après vous être connecté à Oracle, connecté à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], et définir le projet et les options de mappage de données, vous pouvez convertir des objets de base de données Oracle à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objets de base de données.  
  
## <a name="the-conversion-process"></a>Le processus de Conversion  
Convertir des objets de base de données accepte les définitions d’objets à partir d’Oracle, les convertit en similaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objets et charge ensuite ces informations dans les métadonnées SSMA. Il ne charge pas les informations dans l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez ensuite afficher les objets et leurs propriétés à l’aide de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées.  
  
Lors de la conversion, SSMA imprime les messages de sortie dans le volet de sortie et messages d’erreur vers le volet Liste d’erreurs. Utilisez les informations de sortie et d’erreur pour déterminer si vous devez modifier vos bases de données Oracle ou de votre processus de conversion pour obtenir les résultats de la conversion souhaitée.  
  
## <a name="setting-conversion-options"></a>Définition des Options de Conversion  
Avant de convertir des objets, passez en revue les options de conversion de projet dans le **paramètres du projet** boîte de dialogue. À l’aide de cette boîte de dialogue, vous pouvez définir comment SSMA convertit les fonctions et variables globales. Pour plus d’informations, consultez [paramètres du projet &#40;Conversion&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-conversion-oracletosql.md).  
  
## <a name="conversion-results"></a>Résultats de la conversion  
Le tableau suivant présente les objets d’Oracle sont convertis et résultant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objets :  
  
|||  
|-|-|  
|Objets Oracle|Objets SQL Server qui en résulte|  
|Fonctions|Si la fonction peut être directement convertie en [!INCLUDE[tsql](../../includes/tsql-md.md)], SSMA crée une fonction.<br /><br />Dans certains cas, la fonction doit être convertie à une procédure stockée. Dans ce cas, SSMA crée une procédure stockée et une fonction qui appelle la procédure stockée.|  
|Procédures|Si la procédure peut être directement convertie en [!INCLUDE[tsql](../../includes/tsql-md.md)], SSMA crée une procédure stockée.<br /><br />Dans certains cas, une procédure stockée doit être appelée dans une transaction autonome. Dans ce cas, SSMA crée deux procédures stockées : celui qui implémente la procédure et une autre qui est utilisée pour appeler l’implémentation d’une procédure stockée.|  
|.|SSMA crée un ensemble de procédures stockées et fonctions sont unifiées par des noms d’objet similaires.|  
|Séquences|SSMA crée des objets de séquence (SQL Server 2012 ou SQL Server 2014) ou émule les séquences Oracle.|  
|Tables avec des objets dépendants, tels que les index et déclencheurs|SSMA crée des tables avec des objets dépendants.|  
|Afficher les objets dépendants, tels que des déclencheurs|SSMA crée des vues avec des objets dépendants.|  
|Vues matérialisées|**SSMA crée des vues indexées sur SQL server à quelques exceptions près. Conversion échoue si la vue matérialisée inclut un ou plusieurs des constructions suivantes :**<br /><br />Fonction définie par l'utilisateur<br /><br />Champ non déterministe / fonction / expression dans une instruction SELECT, où ou les clauses GROUP BY<br /><br />L’utilisation de la colonne de type Float dans SELECT *, où les clauses GROUP BY (cas spécial de problème précédent) ou<br /><br />(Tables incluses imbriqués) de type de données personnalisées<br /><br />COUNT (distinct &lt;champ&gt;)<br /><br />FETCH<br /><br />Jointures OUTER (LEFT, RIGHT ou FULL)<br /><br />Sous-requête, autre vue<br /><br />DE PLUS, RANK, PROSPECT, OUVRIR UNE SESSION<br /><br />MIN, MAX<br /><br />UNION, LE SIGNE MOINS, SE CROISENT<br /><br />HAVING|  
|Déclencheur|**SSMA crée des déclencheurs selon les règles suivantes :**<br /><br />AVANT la conversion des déclencheurs aux déclencheurs INSTEAD OF.<br /><br />Déclencheurs AFTER sont converties en déclencheurs AFTER.<br /><br />Les déclencheurs INSTEAD OF sont convertis en déclencheurs INSTEAD OF. Plusieurs déclencheurs INSTEAD OF définis sur la même opération sont combinés en un seul déclencheur.<br /><br />Les déclencheurs au niveau des lignes sont émulés à l’aide des curseurs.<br /><br />Les déclencheurs en cascade sont convertis en plusieurs déclencheurs individuels.|  
|Synonymes|**Les synonymes sont créés pour les types d’objet suivants :**<br /><br />Tables et des tables d’objets<br /><br />Vues et les vues de l’objet<br /><br />Procédures stockées<br /><br />Fonctions<br /><br />**Synonymes pour les objets suivants sont résolues et remplacées par des références d’objet direct :**<br /><br />Séquences<br /><br />.<br /><br />Objets de schéma de classe Java<br /><br />Types d’objets définis par l’utilisateur<br /><br />Synonymes d’un autre synonyme ne peuvent pas être migrés et seront marqués comme des erreurs.<br /><br />Synonymes ne sont pas créés pour les vues Materialized.|  
|Types définis par l’utilisateur|**SSMA ne fournit pas de prise en charge pour la conversion des types de défini par l’utilisateur. Types définis par l’utilisateur, y compris son utilisation dans les programmes PL/SQL sont marqués avec des erreurs de conversion spéciale guidés par les règles suivantes :**<br /><br />Colonne de table d’un type défini par l’utilisateur est convertie en varchar (8000).<br /><br />Type défini par l’argument de l’utilisateur à une procédure stockée ou fonction est convertie en varchar (8000).<br /><br />Variable de type défini par l’utilisateur dans le bloc de PL/SQL est convertie en varchar (8000).<br /><br />Objet Table est convertie en une table Standard.<br /><br />Affichage de l’objet est converti en une vue Standard.|  
  
## <a name="converting-oracle-database-objects"></a>Convertir des objets de base de données Oracle  
Pour convertir des objets de base de données Oracle, vous sélectionnez d’abord les objets que vous souhaitez convertir, puis SSMA effectuer la conversion. Pour afficher les messages de sortie pendant la conversion, sur le **vue** menu, sélectionnez **sortie**.  
  
**Pour convertir des objets Oracle à la syntaxe de SQL Server**  
  
1.  Dans l’Explorateur de métadonnées d’Oracle, le serveur Oracle, puis **schémas**.  
  
2.  Sélectionnez les objets à convertir :  
  
    -   Pour convertir tous les schémas, sélectionnez la case à cocher à côté **schémas**.  
  
    -   Pour convertir ou omettre une base de données, sélectionnez la case à cocher en regard du nom de schéma.  
  
    -   Pour convertir ou omettre une catégorie d’objets, développez un schéma, puis sélectionnez ou désactivez la case à cocher en regard de la catégorie.  
  
    -   Pour convertir ou omettre des objets, développez le dossier de catégorie, puis sélectionnez ou désactivez la case à cocher en regard de l’objet.  
  
3.  Pour convertir tous les objets sélectionnés, cliquez sur **schémas** et sélectionnez **convertir le schéma**.  
  
    Vous pouvez également convertir des objets individuels ou des catégories d’objets en double-cliquant sur l’objet ou son dossier parent, puis en sélectionnant **convertir le schéma**.  
  
## <a name="viewing-conversion-problems"></a>Affichage des problèmes de Conversion  
Certains objets Oracle ne peuvent pas être converties. Vous pouvez déterminer le taux de réussite de la conversion en affichant le rapport de synthèse de conversion.  
  
**Pour afficher un rapport de synthèse**  
  
1.  Dans l’Explorateur de métadonnées d’Oracle, sélectionnez **schémas**.  
  
2.  Dans le volet droit, sélectionnez le **rapport** onglet.  
  
    Ce rapport affiche le rapport d’évaluation de résumé pour tous les objets de base de données qui ont été évaluées ou converti. Vous pouvez également afficher un rapport de synthèse pour des objets individuels :  
  
    -   Pour afficher le rapport pour un schéma individuel, sélectionnez le schéma dans l’Explorateur de métadonnées d’Oracle.  
  
    -   Pour afficher le rapport pour un objet individuel, sélectionnez l’objet dans l’Explorateur de métadonnées d’Oracle. Les objets qui présentent des problèmes de conversion ont une icône d’erreur rouge.  
  
Pour les objets en échec de conversion, vous pouvez afficher la syntaxe qui a entraîné l’échec de conversion.  
  
**Pour afficher les problèmes de conversion individuels**  
  
1.  Dans l’Explorateur de métadonnées d’Oracle, développez **schémas**.  
  
2.  Développez le schéma qui affiche une icône d’erreur rouge.  
  
3.  Sous le schéma, développez un dossier qui a une icône d’erreur rouge.  
  
4.  Sélectionnez l’objet qui a une icône d’erreur rouge.  
  
5.  Dans le volet droit, cliquez sur le **rapport** onglet.  
  
6.  En haut de la **rapport** onglet est une liste déroulante. Si la liste affiche **statistiques**, modifiez la sélection à **Source**.  
  
    SSMA affichera le code source et plusieurs boutons immédiatement au-dessus du code.  
  
7.  Cliquez sur le **problème suivant** bouton. Il s’agit d’une icône d’erreur rouge avec une flèche qui pointe vers la droite.  
  
    SSMA met en évidence le premier code source problématiques qu’il trouve dans l’objet actuel.  
  
Pour chaque élément qui ne peut pas être converti, vous devez déterminer ce que vous voulez faire avec cet objet :  
  
-   Vous pouvez modifier le code source pour les procédures sur le **SQL** onglet.  
  
-   Vous pouvez modifier l’objet dans la base de données Oracle pour supprimer ou de réviser le code problématique. Pour charger le code mis à jour dans SSMA, vous devrez mettre à jour les métadonnées. Pour plus d’informations, consultez [connexion à la base de données Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-oracle-database-oracletosql.md).  
  
-   Vous pouvez exclure l’objet de la migration. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées et l’Explorateur de métadonnées d’Oracle, désactivez la case à cocher en regard de l’élément avant de charger les objets vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et migration des données à partir d’Oracle.  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante du processus de migration consiste à [charger les objets convertis dans SQL Server](loading-converted-database-objects-into-sql-server-oracletosql.md).  
  
## <a name="see-also"></a>Voir aussi  
[Bases de données de migration d’Oracle vers SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
