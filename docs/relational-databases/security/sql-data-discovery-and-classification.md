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
ms.date: 06/25/2019
ms.author: mibar
author: barmichal
manager: craigg
ms.openlocfilehash: b45f3a081b7be55642e662ed195cfc1377e3659b
ms.sourcegitcommit: 20d24654e056561fc33cadc25eca8b4e7f214b1b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67351730"
---
# <a name="sql-data-discovery-and-classification"></a>Découverte et classification des données SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

La fonctionnalité Découverte et classification des données introduit un nouvel outil intégré à SQL Server Management Studio (SSMS) pour la **découverte**, la **classification**, **l’étiquetage** &  la **création de rapport** concernant les données sensibles dans vos bases de données.
La découverte et la classification de vos données les plus sensibles (professionnelles, financières, médicales, etc.) peuvent jouer un rôle essentiel dans la protection des informations de votre organisation. Cette fonctionnalité peut servir d’infrastructure pour :
* Contribuer à répondre aux normes de confidentialité des données.
* Contrôler l’accès aux bases de données/colonnes contenant des données sensibles et en renforcer la sécurité.

> [!NOTE]
> La fonctionnalité Découverte et classification des données est **prise en charge pour SQL Server 2008 et versions ultérieures et peut être utilisée avec SSMS 17.5 ou versions ultérieures**. Pour Azure SQL Database, consultez [Découverte et classification des données Azure SQL Database](https://go.microsoft.com/fwlink/?linkid=866265).

## <a id="subheading-1"></a>Vue d'ensemble
La fonctionnalité Découverte et classification des données introduit un ensemble de services avancées, qui forment un nouveau paradigme de protection des informations SQL visant à protéger les données et pas seulement la base de données :
* **Découverte et recommandations** : le moteur de classification analyse votre base de données et identifie les colonnes contenant des données potentiellement sensibles. Il fournit ensuite un moyen simple d’examiner et appliquer les recommandations de classification appropriée, ainsi que de classifier manuellement des colonnes.
* **Étiquetage** : des étiquettes de classification de sensibilité peuvent être marquées de manière permanente sur les colonnes.
* **Visibilité** : L’état de classification de la base de données peut être consulté dans un rapport détaillé imprimable/exportable à utiliser à des fins de conformité et d’audit, ainsi que pour d’autres besoins.

## <a id="subheading-2"></a>Découverte, classification et étiquetage des colonnes sensibles
La section suivante décrit les étapes de découverte, classification et étiquetage des colonnes contenant des données sensibles dans votre base de données, ainsi que l’affichage de l’état de classification actuel de votre base de données et l’exportation de rapports.

La classification comprend deux attributs de métadonnées :
* Étiquettes : principaux attributs de classification utilisés pour définir le niveau de sensibilité des données stockées dans la colonne.  
* Types d’informations : fournissent un niveau de granularité supplémentaire dans le type de données stockées dans la colonne.

**Pour classifier votre base de données SQL Server :**

1. Dans SQL Server Management Studio (SSMS), connectez-vous à SQL Server.

2. Dans l’Explorateur d’objets SSMS, cliquez avec le bouton droit sur la base de données à classifier et choisissez **Tâches** > **Classifier les données...** .

    ![Volet de navigation][1]

3. Le moteur de classification analyse votre base de données pour identifier les colonnes contenant des données potentiellement sensibles et fournit la liste des **classifications de colonne recommandées** :

    * Pour consulter la liste des classifications de colonne recommandées, cliquez sur la zone de notification des recommandations en haut ou sur le panneau de recommandations en bas de la fenêtre :

        ![Volet de navigation][2]

        ![Volet de navigation][3]

    * Passez en revue la liste des recommandations :
        * Pour accepter une recommandation associée à une colonne spécifique, cochez la case dans la colonne de gauche de la ligne concernée. Vous pouvez aussi accepter *toutes les recommandations* en cochant la case dans l’en-tête du tableau de recommandations.

        * Vous pouvez changer le type d’informations et l’étiquette de sensibilité recommandés à l’aide des zones de liste déroulante.        

        ![Volet de navigation][4]

    * Pour appliquer les recommandations sélectionnées, cliquez sur le bouton bleu **Accepter les recommandations sélectionnées**.

        ![Volet de navigation][5]

4. Vous pouvez aussi **classifier manuellement** les colonnes à la place ou en plus de la classification basée sur les recommandations :

    * Cliquez sur **Ajouter une classification** dans le menu supérieur de la fenêtre.

        ![Volet de navigation][6]

    * Dans la fenêtre contextuelle qui s’ouvre, sélectionnez le schéma > table > colonne à classifier ainsi que le type d’informations et l’étiquette de sensibilité. Ensuite, cliquez sur le bouton bleu **Ajouter une classification**, en bas de la fenêtre contextuelle.

        ![Volet de navigation][7]

5. Pour terminer votre classification et étiqueter de manière permanente (balise) les colonnes de la base de données avec les nouvelles métadonnées de classification, cliquez sur **Enregistrer** dans le menu supérieur de la fenêtre.

    ![Volet de navigation][8]


6. Pour générer un rapport avec un récapitulatif complet de l’état de classification de la base de données, cliquez sur **Afficher le rapport** dans le menu supérieur de la fenêtre.

    ![Volet de navigation][9]

    ![Volet de navigation][10]


## <a id="subheading-3"></a>Accès aux métadonnées de classification

Les métadonnées de classification des *types d’informations* et des *étiquettes de sensibilité* sont stockées dans les propriétés étendues suivantes : 
* sys_information_type_name
* sys_sensitivity_label_name

Les métadonnées sont accessibles à l’aide de l’affichage catalogue [sys.extended_properties](https://docs.microsoft.com/sql/relational-databases/system-catalog-views/extended-properties-catalog-views-sys-extended-properties) dans les propriétés étendues.

L’exemple de code suivant retourne toutes les colonnes classifiées avec leurs classifications correspondantes :

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

## <a id="subheading-4"></a>Étapes suivantes

Pour Azure SQL Database, consultez [Découverte et classification des données Azure SQL Database](https://go.microsoft.com/fwlink/?linkid=866265).

Protégez vos colonnes sensibles en appliquant des mécanismes de sécurité au niveau des colonnes :

* [Dynamic Data Masking](https://docs.microsoft.com/sql/relational-databases/security/dynamic-data-masking) pour masquer les colonnes sensibles en cours d’utilisation.
* [Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine) pour chiffrer les colonnes sensibles au repos.

<!--Anchors-->
[SQL Data Discovery & Classification overview]: #subheading-1
[Discovering, classifying & labeling sensitive columns]: #subheading-2
[Accessing the classification metadata]: #subheading-3
[Next Steps]: #subheading-4

<!--Image references-->
[1]: ./media/sql-data-discovery-and-classification/1_data_classification_explorer_menu.png
[2]: ./media/sql-data-discovery-and-classification/2_recommendations_notification_box.png
[3]: ./media/sql-data-discovery-and-classification/3_recommendations_panel.png
[4]: ./media/sql-data-discovery-and-classification/4_recommendations.png
[5]: ./media/sql-data-discovery-and-classification/5_accept_recommendations_button.png
[6]: ./media/sql-data-discovery-and-classification/6_add_classification_button.png
[7]: ./media/sql-data-discovery-and-classification/7_manual_classification.png
[8]: ./media/sql-data-discovery-and-classification/8_save.png
[9]: ./media/sql-data-discovery-and-classification/9_view_report.png
[10]: ./media/sql-data-discovery-and-classification/10_report.png
