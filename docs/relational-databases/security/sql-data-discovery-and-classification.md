---
title: Découverte et classification des données SQL | Microsoft Docs
description: Découverte et classification des données SQL
documentationcenter: ''
ms.reviewer: vanto
ms.assetid: 89c2a155-c2fb-4b67-bc19-9b4e03c6d3bc
ms.service: sql-database
ms.prod_service: sql-database,sql
ms.custom: security
ms.topic: conceptual
ms.date: 09/12/2019
ms.author: mibar
author: barmichal
ms.openlocfilehash: 077a9a6be533ec05f9c062100d04bf02562f6066
ms.sourcegitcommit: 4933934fad9f3c3e16406952ed964fbd362ee086
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75548344"
---
# <a name="sql-data-discovery-and-classification"></a>Découverte et classification des données SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

La fonctionnalité Découverte et classification des données introduit un nouvel outil intégré à [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) pour la **découverte**, la **classification**, l’**étiquetage**  &  la **création de rapport** concernant les données sensibles dans vos bases de données.
La découverte et la classification de vos données les plus sensibles (professionnelles, financières, médicales, etc.) peuvent jouer un rôle essentiel dans la protection des informations de votre organisation. Elles peuvent servir d’infrastructure pour :
* Contribuer à répondre aux normes de confidentialité des données.
* Contrôler l’accès aux bases de données/colonnes contenant des données sensibles et en renforcer la sécurité.

> [!NOTE]
> La fonctionnalité Découverte et classification des données est **prise en charge pour SQL Server 2012 et ultérieur et peut être utilisée avec [SSMS 17.5](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) ou ultérieur**. Pour Azure SQL Database, consultez [Découverte et classification des données Azure SQL Database](/azure/sql-database/sql-database-data-discovery-and-classification/).

## <a id="subheading-1"></a>Vue d’ensemble
La fonctionnalité Découverte et classification des données introduit un ensemble de services avancées, qui forment un nouveau paradigme de protection des informations SQL visant à protéger les données et pas seulement la base de données :

* **Découverte et recommandations** : le moteur de classification analyse votre base de données et identifie les colonnes contenant des données potentiellement sensibles. Il fournit ensuite un moyen simple d’examiner et appliquer les recommandations de classification appropriée, ainsi que de classifier manuellement des colonnes.
* **Étiquetage** : des étiquettes de classification de sensibilité peuvent être marquées de manière permanente sur les colonnes.
* **Visibilité** : L’état de classification de la base de données peut être consulté dans un rapport détaillé imprimable/exportable à utiliser à des fins de conformité et d’audit, ainsi que pour d’autres besoins.

## <a id="subheading-2"></a>Découverte, classification et étiquetage des colonnes sensibles
La section suivante décrit les étapes de découverte, de classification et d’étiquetage des colonnes contenant des données sensibles dans votre base de données, ainsi que l’affichage de l’état actuel de la classification de votre base de données et l’exportation de rapports.

La classification comprend deux attributs de métadonnées :
* Étiquettes : principaux attributs de classification utilisés pour définir le niveau de sensibilité des données stockées dans la colonne.  
* Types d’informations : fournissent un niveau de granularité supplémentaire dans le type de données stockées dans la colonne.

**Pour classifier votre base de données SQL Server :**

1. Dans SQL Server Management Studio (SSMS), connectez-vous à SQL Server.

2. Dans l’Explorateur d’objets SSMS, cliquez avec le bouton droit sur la base de données à classifier et choisissez **Tâches** > **Découverte et classification des données** > **Classifier les données**.

   ![Volet de navigation][0]

3. Le moteur de classification analyse votre base de données pour identifier les colonnes contenant des données potentiellement sensibles et fournit la liste des **classifications de colonne recommandées** :

    * Pour consulter la liste des classifications de colonne recommandées, cliquez sur la zone de notification des recommandations en haut ou sur le panneau de recommandations en bas de la fenêtre :

        ![Volet de navigation][2]

        ![Volet de navigation][3]

    * Passez en revue la liste des recommandations :
        * Pour accepter une recommandation associée à une colonne spécifique, cochez la case dans la colonne de gauche de la ligne concernée. Vous pouvez également accepter *toutes les recommandations* en cochant la case dans l’en-tête de table de recommandations.

        * Vous pouvez changer le type d’informations et l’étiquette de sensibilité recommandés à l’aide des zones de liste déroulante.        

        ![Volet de navigation][4]

    * Pour appliquer les recommandations sélectionnées, cliquez sur le bouton bleu **Accepter les recommandations sélectionnées**.

        ![Volet de navigation][5]

4. Vous pouvez aussi, en guise d’alternative, **classifier manuellement** des colonnes ou, en plus de la classification basée sur les recommandations :

    * Cliquez sur **Ajouter une classification** dans le menu en haut de la fenêtre.

        ![Volet de navigation][6]

    * Dans la fenêtre contextuelle qui apparaît, sélectionnez le schéma > table > colonne que vous souhaitez classifier, ainsi que l’étiquette de sensibilité et le type d’informations. Cliquez sur le bouton bleu **Ajouter une classification** en bas de la fenêtre contextuelle.

        ![Volet de navigation][7]

5. Pour terminer votre classification et étiqueter de manière permanente les colonnes de base de données avec les nouvelles métadonnées de classification, cliquez sur **Enregistrer** dans le menu en haut de la fenêtre.

    ![Volet de navigation][8]


6. Pour générer un rapport avec un récapitulatif complet de l’état de classification de la base de données, cliquez sur **Afficher le rapport** dans le menu supérieur de la fenêtre. (Vous pouvez également générer un rapport à l’aide de SSMS. Cliquez avec le bouton droit sur la base de données dans laquelle vous souhaitez générer le rapport, puis choisissez **Tâches** > **Découverte et classification des données** > **Générer le rapport**.)

    ![Volet de navigation][9]

    ![Volet de navigation][10]

## <a id="subheading-3"></a>Gérer la stratégie de protection des informations avec SSMS

Vous pouvez gérer la stratégie de protection des informations à l’aide de [SSMS 18.4](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) ou ultérieur :

1. Dans SQL Server Management Studio (SSMS), connectez-vous à SQL Server.

2. Dans l’Explorateur d’objets SSMS, cliquez avec le bouton droit sur l’une de vos bases de données et choisissez **Tâches** > **Découverte et classification des données**.

   Les options de menu suivantes vous permettent de gérer la stratégie de protection des informations :

* **Définir la stratégie de protection des informations** : utilise la stratégie de protection des informations telle que définie dans le fichier JSON sélectionné.

* **Exporter la stratégie de protection des informations** : exporte la stratégie de protection des informations dans un fichier JSON.

* **Réinitialiser la stratégie de protection des informations** : rétablit la stratégie de protection des informations par défaut.

> [!IMPORTANT]
> Le fichier de stratégie de protection des informations n’est pas stocké dans l’ordinateur SQL Server.
> SSMS utilise une stratégie de protection des informations par défaut. Si une stratégie de protection des informations personnalisée échoue, SSMS ne peut pas utiliser la stratégie par défaut. La classification des données échoue. Pour résoudre ce problème, cliquez sur **Réinitialiser la stratégie de protection des informations** pour utiliser la stratégie par défaut et réactiver la classification des données.

## <a id="subheading-4"></a>Accès aux métadonnées de classification

SQL Server 2019 introduit la vue de catalogue système [`sys.sensitivity_classifications`](../system-catalog-views/sys-sensitivity-classifications-transact-sql.md). Cette vue retourne les types d’informations et les étiquettes de sensibilité. 

> [!NOTE]
> Cette vue nécessite l’autorisation **VIEW ANY SENSITIVITY CLASSIFICATION**. Pour plus d'informations, consultez [Metadata Visibility Configuration](https://docs.microsoft.com/sql/relational-databases/security/metadata-visibility-configuration?view=sql-server-ver15).

Sur les instances SQL Server 2019, interrogez `sys.sensitivity_classifications` pour passer en revue toutes les colonnes classifiées avec leurs classifications correspondantes. Par exemple : 

```sql
SELECT 
    schema_name(O.schema_id) AS schema_name,
    O.NAME AS table_name,
    C.NAME AS column_name,
    information_type,
    label
FROM sys.sensitivity_classifications sc
    JOIN sys.objects O
    ON  sc.major_id = O.object_id
    JOIN sys.columns C 
    ON  sc.major_id = C.object_id  AND sc.minor_id = C.column_id
```

Avant SQL Server 2019, les métadonnées de classification des types d’informations et des étiquettes de sensibilité se trouvaient dans les propriétés étendues suivantes : 

* `sys_information_type_name`
* `sys_sensitivity_label_name`

Les métadonnées sont accessibles par le biais de la vue catalogue [`sys.extended_properties`](../system-catalog-views/extended-properties-catalog-views-sys-extended-properties.md) dans les propriétés étendues.

Pour les instances de SQL Server 2017 et versions antérieures, l’exemple suivant retourne toutes les colonnes classifiées avec leurs classifications correspondantes :

```sql
SELECT
    schema_name(O.schema_id) AS schema_name,
    O.NAME AS table_name,
    C.NAME AS column_name,
    information_type,
    sensitivity_label 
FROM
    (
        SELECT
            IT.major_id,
            IT.minor_id,
            IT.information_type,
            L.sensitivity_label 
        FROM
        (
            SELECT
                major_id,
                minor_id,
                value AS information_type 
            FROM sys.extended_properties 
            WHERE NAME = 'sys_information_type_name'
        ) IT 
        FULL OUTER JOIN
        (
            SELECT
                major_id,
                minor_id,
                value AS sensitivity_label 
            FROM sys.extended_properties 
            WHERE NAME = 'sys_sensitivity_label_name'
        ) L 
        ON IT.major_id = L.major_id AND IT.minor_id = L.minor_id
    ) EP
    JOIN sys.objects O
    ON  EP.major_id = O.object_id 
    JOIN sys.columns C 
    ON  EP.major_id = C.object_id AND EP.minor_id = C.column_id
```

## <a id="subheading-5"></a>Gérer les classifications

# <a name="t-sqltabt-sql"></a>[T-SQL](#tab/t-sql)
Vous pouvez utiliser T-SQL pour ajouter/supprimer des classifications de colonne, ainsi que pour récupérer toutes les classifications pour la base de données entière.

- Ajouter/Mettre à jour la classification d’une ou plusieurs colonnes : [ADD SENSITIVITY CLASSIFICATION](https://docs.microsoft.com/sql/t-sql/statements/add-sensitivity-classification-transact-sql)
- Supprimer la classification d’une ou plusieurs colonnes : [DROP SENSITIVITY CLASSIFICATION](https://docs.microsoft.com/sql/t-sql/statements/drop-sensitivity-classification-transact-sql)

# <a name="powershell-cmdlettabsql-powelshell"></a>[Applet de commande PowerShell](#tab/sql-powelshell)
Vous pouvez utiliser l’applet de commande PowerShell pour ajouter/supprimer des classifications de colonne, ainsi que pour récupérer toutes les classifications et obtenir des recommandations pour la base de données entière.

- [Get-SqlSensitivityClassification](https://docs.microsoft.com/powershell/module/sqlserver/Get-SqlSensitivityClassification?view=sqlserver-ps)
- [Get-SqlSensitivityRecommendations](https://docs.microsoft.com/powershell/module/sqlserver/Get-SqlSensitivityRecommendations?view=sqlserver-ps)
- [Set-SqlSensitivityClassification](https://docs.microsoft.com/powershell/module/sqlserver/Set-SqlSensitivityClassification?view=sqlserver-ps)
- [Remove-SqlSensitivityClassification](https://docs.microsoft.com/powershell/module/sqlserver/Remove-SqlSensitivityClassification?view=sqlserver-ps)

---

## <a id="subheading-6"></a>Étapes suivantes

Pour Azure SQL Database, consultez [Découverte et classification des données Azure SQL Database](https://go.microsoft.com/fwlink/?linkid=866265).

Protégez vos colonnes sensibles en appliquant des mécanismes de sécurité au niveau des colonnes :

* [Dynamic Data Masking](https://docs.microsoft.com/sql/relational-databases/security/dynamic-data-masking) pour masquer les colonnes sensibles en cours d’utilisation.
* [Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine) pour chiffrer les colonnes sensibles au repos.

<!--Anchors-->
[SQL Data Discovery & Classification overview]: #subheading-1
[Discovering, classifying & labeling sensitive columns]: #subheading-2
[Manage information protection policy with SSMS]: #subheading-3
[Accessing the classification metadata]: #subheading-4
[Manage classifications]: #subheading-5
[Next Steps]: #subheading-6

<!--Image references-->

[0]: ./media/sql-data-discovery-and-classification/0-data-classification-explorer.png
[2]: ./media/sql-data-discovery-and-classification/2-recommendations-notification-box.png
[3]: ./media/sql-data-discovery-and-classification/3-recommendations-panel.png
[4]: ./media/sql-data-discovery-and-classification/4-recommendations.png
[5]: ./media/sql-data-discovery-and-classification/5-accept-recommendations-button.png
[6]: ./media/sql-data-discovery-and-classification/6-add-classification-button.png
[7]: ./media/sql-data-discovery-and-classification/7-manual-classification.png
[8]: ./media/sql-data-discovery-and-classification/8-save.png
[9]: ./media/sql-data-discovery-and-classification/9-view-report.png
[10]: ./media/sql-data-discovery-and-classification/10-report.png
