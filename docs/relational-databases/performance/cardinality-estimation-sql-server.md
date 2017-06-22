---
title: "Évaluation de la cardinalité (SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 10/04/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cardinality estimator
- CE (cardinality estimator)
- estimating cardinality
ms.assetid: baa8a304-5713-4cfe-a699-345e819ce6df
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e6ef57f8467e87b97024fc08b4916ac4f8e7752b
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="cardinality-estimation-sql-server"></a>Évaluation de la cardinalité (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  
Cet article explique comment évaluer et choisir la meilleure configuration d’estimation de la cardinalité pour votre système SQL. La plupart des systèmes bénéficient de la dernière version de l’estimation de la cardinalité, car il s’agit de la plus précise. L’estimation de la cardinalité prédit le nombre de lignes que votre requête est susceptible de renvoyer. La prédiction de la cardinalité est utilisée par l’optimiseur de requête pour générer un plan de requête optimal. En général, plus l’estimation de la cardinalité est précise, meilleur est le plan de requête.  
  
Le système d’applications peut contenir une requête importante dont le plan est remplacé par un plan plus lent en raison de la nouvelle estimation de la cardinalité. Voici quelques exemples d’une telle requête :  
  
- Une requête OLTP qui s’exécute si souvent que plusieurs instances de cette requête s’exécutent simultanément.  
- Une instruction SELECT avec une agrégation importante qui s’exécute pendant vos heures de travail OLTP.  
  
Vous disposez de techniques pour identifier une requête qui s’exécute plus lentement avec la nouvelle estimation de cardinalité. Vous disposez d’options pour résoudre les problèmes de performances.  
  
  
## <a name="versions-of-the-ce"></a>Versions de l’estimation de cardinalité  
  
 En 1998, une mise à jour majeure de l’estimation de cardinalité a été intégrée à Microsoft SQL Server 7.0, pour lequel le niveau de compatibilité était de 70. Les mises à jour suivantes ont été intégrées à [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016, ce qui signifie que les niveaux de compatibilité sont de 120 et 130. Les mises à jour de l’estimation de cardinalité pour les niveaux 120 et 130 comprennent des hypothèses et des algorithmes qui fonctionnent bien avec les charges de travail d’entreposage de données modernes et avec OLTP (traitement transactionnel en ligne).  
  
 **Niveau de compatibilité** : Vous pouvez vérifier le niveau de votre base de données à l’aide du code Transact-SQL suivant pour [COMPATIBILITY_LEVEL](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  

```tsql  
SELECT ServerProperty('ProductVersion');  
go  
  
ALTER DATABASE <yourDatabase>  
    SET COMPATIBILITY_LEVEL = 130;  
go  
  
SELECT    d.name, d.compatibility_level  
    FROM  sys.databases AS d  
    WHERE d.name = 'yourDatabase';  
go  
```  
  
 Pour une base de données SQL Server définie au niveau de compatibilité 120, l’activation de l’indicateur de trace 9481 force le système à utiliser le niveau 70 de l’estimation de la cardinalité .  
  
 **Estimation de cardinalité héritée** : Pour une base de données SQL Server définie au niveau de compatibilité 130, le niveau 70 de l’estimation de la cardinalité peut être activé à l’aide de l’instruction Transact-SQL suivante concernant [SCOPED CONFIGURATION](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) .
  
```tsql  
ALTER DATABASE
    SCOPED CONFIGURATION  
        SET LEGACY_CARDINALITY_ESTIMATION = ON;  
go  
  
SELECT  name, value  
    FROM  sys.database_scoped_configurations  
    WHERE name = 'LEGACY_CARDINALITY_ESTIMATION';  
```  
  
 **Magasin de requêtes**: Si vous utilisez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016, le magasin de requêtes est un outil pratique pour l’examen des performances de vos requêtes.  Dans SQL Server Management Studio (SSMS.exe), dans **l’Explorateur d’objets** situé sous le nœud de votre base de données, le nœud **Magasin de requêtes** s’affiche lorsque le magasin de requêtes est activé.  
  
```tsql  
ALTER DATABASE <yourDatabase>  
    SET QUERY_STORE = ON;  
go  
  
SELECT  
        q.actual_state_desc    AS [actual_state_desc-ofQueryStore],  
        q.desired_state_desc,  
        q.query_capture_mode_desc  
    FROM  
        sys.database_query_store_options  AS q;  
go  
  
ALTER DATABASE <yourDatabase>  
    SET QUERY_STORE CLEAR;  
```  
  
 *Conseil* : Il est recommandé d’installer la dernière version de [(SSMS.exe)](http://msdn.microsoft.com/library/mt238290.aspx)tous les mois.  
  
 Pour effectuer le suivi des prédictions de cardinalité, vous pouvez utiliser l’événement étendu nommé **query_optimizer_estimate_cardinality**.  L’exemple de code T-SQL suivant s’exécute sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Un fichier .xel est écrit dans C:\Temp\ (vous pouvez modifier ce chemin). Lorsque vous ouvrez le fichier .xel dans SSMS, vous voyez des informations détaillées le concernant.  
  
```tsql  
DROP EVENT SESSION Test_the_CE_qoec_1 ON SERVER;  
go  
  
CREATE EVENT SESSION Test_the_CE_qoec_1  
    ON SERVER  
    ADD EVENT sqlserver.query_optimizer_estimate_cardinality  
    (  
        ACTION (sqlserver.sql_text)  
            WHERE (  
                sql_text LIKE '%yourTable%'  
                and sql_text LIKE '%SUM(%'  
            )  
    )  
    ADD TARGET package0.asynchronous_file_target   
        (SET  
            filename = 'c:\temp\xe_qoec_1.xel',  
            metadatafile = 'c:\temp\xe_qoec_1.xem'  
        );  
go  
  
ALTER EVENT SESSION Test_the_CE_qoec_1  
    ON SERVER  
    STATE = START;  --STOP;  
go  
```  
  
 Pour plus d’informations sur les événements étendus adaptés à Azure SQL Database, consultez [Événements étendus dans la base de données SQL](http://azure.microsoft.com/documentation/articles/sql-database-xevent-db-diff-from-svr/).  
  
  
## <a name="steps-to-assess-the-ce-version"></a>Étapes d’évaluation de la version d’estimation de la cardinalité  
  
 Les étapes suivantes permettent d’évaluer si l’une de vos requêtes importantes est moins performante avec la dernière version de l’estimation de cardinalité. Certaines étapes sont effectuées en exécutant l’exemple de code présenté dans la section précédente.  
  
1.  Ouvrez SSMS. Vérifiez que le niveau de compatibilité de votre base de données  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]est configuré sur la valeur maximale.  
  
2.  Effectuez les étapes préliminaires suivantes :  
  
    1.  Ouvrez SSMS.  
  
    2.  Exécutez le code T-SQL pour vérifier que le niveau de compatibilité de votre base de données  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré sur la valeur maximale.  
  
    3.  Vérifiez dans votre base de données que la configuration LEGACY_CARDINALITY_ESTIMATION est désactivée.  
  
    4.  Supprimez le contenu de votre magasin de requêtes. Vérifiez bien entendu que votre magasin de requêtes est activé.  
  
    5.  Exécutez l’instruction \`SET NoCount OFF;`  
  
3.  Exécutez l’instruction \`SET STATISTICS XML ON;`  
  
4.  Exécutez votre requête importante.  
  
5.  Dans le volet de résultats, sous l’onglet **Messages** , notez le nombre de lignes affectées.  
  
6.  Dans le volet de résultats de l’onglet **Résultats** , double-cliquez sur la cellule qui contient les statistiques au format XML. Un plan de requête graphique s’affiche.  
  
7.  Cliquez avec le bouton droit sur la première zone du plan de requête graphique, puis cliquez sur **Propriétés**.  
  
8.  Notez les valeurs des propriétés suivantes en vue de les comparer ultérieurement avec une configuration différente :  
  
    -   **CardinalityEstimationModelVersion**.  
  
    -   **Nombre de lignes estimé**.  
  
    -   **Coût E/S estimé**, et plusieurs propriétés *estimées* similaires qui impliquent des performances réelles plutôt que des prédictions de nombre de lignes.  
  
    -   **Opération logique** et **Opération physique**. *Parallélisme* est une bonne valeur.  
  
    -   **Mode d’exécution réel**. *Lot* est une bonne valeur, meilleure que *Ligne*.  
  
9. Comparez le nombre estimé de lignes au nombre réel de lignes. Le pourcentage d’inexactitude de l’estimation de la cardinalité est-il de 1 % (haut ou bas) ou de 10 % ?  
  
10. Exécutez \`SET STATISTICS XML OFF;`  
  
11. Exécutez le code T-SQL pour baisser d’un niveau le niveau de compatibilité de votre base de données (par exemple, de 130 à 120).  
  
12. Exécutez à nouveau toutes les étapes non préliminaires.  
  
13. Comparez les valeurs des propriétés de l’estimation de la cardinalité des deux exécutions.  
  
    - Le pourcentage d’inexactitude est-il moins élevé avec la nouvelle estimation de la cardinalité ?  
  
14. Enfin, comparez les différentes valeurs de propriétés de performances des deux exécutions.  
  
    -   Votre requête a-t-elle utilisé un plan différent pour les deux estimations ?  
  
    -   Votre requête s’est-elle exécutée plus lentement sous la dernière version de l’estimation ?  
  
    -   À moins que votre requête ne s’exécute mieux et avec un autre plan sous l’ancienne version de l’estimation de la cardinalité, il est préférable d’utiliser la dernière version.  
  
    -   Toutefois, si votre requête s’exécute avec un plan plus rapide sous l’ancienne version de l’estimation de la cardinalité, envisagez de forcer le système à utiliser le plan plus rapide et à ignorer l’estimation de la cardinalité. Ainsi, vous pourrez disposer de la dernière version de l’estimation de la cardinalité, tout en gardant le plan plus rapide pour les cas exceptionnels.  
  
## <a name="how-to-activate-the-best-query-plan"></a>Comment activer le meilleur plan de requête  
  
Supposons qu’avec la nouvelle estimation de cardinalité, un plan de requête plus lent soit généré pour votre requête. Voici quelques options permettant d’activer le plan plus rapide.  
  
Vous pouvez définir le niveau de compatibilité sur une valeur inférieure à la dernière disponible pour l’ensemble de votre base de données.  
  
- Cela active l’ancienne version de l’estimation, mais soumet toutes les requêtes à la version plus ancienne et moins exacte.  
  
- De plus, l’ancienne version ne possède pas les grandes améliorations qui ont été apportées à l’optimiseur de requête.  
  
LEGACY_CARDINALITY_ESTIMATION vous permet d’utiliser l’ancienne version de l’estimation de la cardinalité pour l’ensemble de la base de données, tout en profitant des améliorations de l’optimiseur de requête.  
  
Pour un plus grand contrôle, vous pouvez *forcer* le système SQL à utiliser le plan généré avec l’ancienne version de l’estimation durant vos tests. Après avoir *épinglé* votre plan par défaut, vous pouvez configurer votre base de données dans son intégralité pour qu’elle utilise le niveau de compatibilité et l’estimation de cardinalité les plus récents. L’utilisation de cette option est développée plus loin dans cette rubrique.  
  
### <a name="how-to-force-a-particular-query-plan"></a>Comment forcer un plan de requête  
  
Le magasin de requêtes vous propose différentes façons de forcer le système à utiliser un plan de requête :  
  
- Exécutez **sp_query_store_force_plan**.  
  
- Dans SSMS, développez le nœud de votre **Magasin de requêtes** , cliquez avec le bouton droit sur **Principaux nœuds consommateurs de ressources**, puis cliquez sur **Afficher les principaux nœuds consommateurs de ressources**. L’affichage montre les boutons **Forcer le plan** et **Annuler l’obligation d’utiliser le plan**.  
  
 Pour plus d’informations sur le magasin de requêtes, consultez [Analyse des performances à l’aide du magasin de requêtes](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md).  
  
  
## <a name="descriptions-of-advance-ce"></a>Descriptions de l’estimation de cardinalité avancée  
  
Cette section contient des exemples de requêtes qui tirent parti des améliorations implémentées dans les versions récentes de l’estimation de la cardinalité. Il s’agit là d’informations générales qui ne nécessitent pas d’intervention de votre part.  
  
### <a name="example-a-ce-understands-maximum-value-might-be-higher-than-when-statistics-were-last-gathered"></a>Exemple A. L’estimation de la cardinalité comprend que la valeur maximale peut être plus élevée que lors de la dernière collecte de statistiques  
  
Supposons que la dernière collecte de statistiques ait eu lieu pour OrderTable le 2016-04-30, lorsque l’OrderAddedDate maximal était 2016-04-30. L’estimation de la cardinalité avec le niveau de compatibilité 120 (et les niveaux plus élevés) comprend que les colonnes d’OrderTable qui comprennent des données *croissantes* peuvent avoir des valeurs supérieures aux valeurs maximales enregistrées par les statistiques. Cette compréhension permet d’améliorer le plan de requête pour les instructions SQL SELECT telles que la suivante.  
  
```tsql  
SELECT CustomerId, OrderAddedDate  
    FROM OrderTable  
    WHERE OrderAddedDate >= '2016-05-01';  
```  
  
### <a name="example-b-ce-understands-that-filtered-predicates-on-the-same-table-are-often-correlated"></a>Exemple B. L’estimation de la cardinalité comprend que les prédicats filtrés sur la même table sont souvent corrélés  
  
Dans l’instruction SELECT suivante, nous voyons les prédicats filtrés sur Make (Constructeur) et Model (Modèle). Nous comprenons intuitivement que quand « Make » (Constructeur) a la valeur « Honda », il est possible que « Model » ait la valeur « Civic », car le constructeur Honda fabrique le modèle Civic.  
  
L’estimation de la cardinalité avec le niveau 120 comprend qu’il peut y avoir une corrélation entre les deux colonnes de la même table (« Make » et « Model »). L’estimation de la cardinalité fait une estimation plus précise du nombre de lignes renvoyées par la requête, et l’optimiseur de requête génère un plan plus optimal.  
  
```tsql  
SELECT Model_Year, Purchase_Price  
    FROM dbo.Cars  
    WHERE  
        Make  = 'Honda'  AND  
        Model = 'Civic';  
```  
  
### <a name="example-c-ce-no-longer-assumes-any-correlation-between-filtered-predicates-from-different-tables"></a>Exemple C. L’estimation de la cardinalité ne suppose plus aucune corrélation entre les prédicats filtrés issus de tables différentes  
  
Grâce à la nouvelle recherche étendue sur les charges de travail modernes, les données métier ont révélé que les filtres de prédicat issus de différentes tables ne sont généralement pas corrélés. Dans la requête suivante, l’estimation de la cardinalité suppose qu’il n’existe aucune corrélation entre s.type et r.date. Par conséquent, l’estimation de la cardinalité obtient une estimation plus basse que le nombre de lignes retournées.  
  
```tsql  
SELECT s.ticket, s.customer, r.store  
    FROM  
                   dbo.Sales    AS s  
        CROSS JOIN dbo.Returns  AS r  
    WHERE  
        s.ticket = r.ticket  AND  
        s.type   = 'toy'     AND  
        r.date   = '2016-05-11';  
```  
  
  
## <a name="see-also"></a>Voir aussi  
 [Surveiller et régler les performances](../../relational-databases/performance/monitor-and-tune-for-performance.md)  
  


