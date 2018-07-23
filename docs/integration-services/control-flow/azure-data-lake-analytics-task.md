---
title: Tâche Azure Data Lake Analytics | Microsoft Docs
ms.custom: ''
ms.date: 05/18/2018
ms.prod: sql
ms.prod_service: integration-services
ms.component: control-flow
ms.reviewer: douglasl
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSTASK.F1
- SQL14.DTS.DESIGNER.AFPADLSTASK.F1
author: yanancai
ms.author: yanacai
manager: craigg
ms.openlocfilehash: 395d790069294aed541f9756fa7caefbb62f9a7b
ms.sourcegitcommit: 44e9bf62f2c75449c17753ed66bf85c43928dbd5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37854423"
---
# <a name="azure-data-lake-analytics-task"></a>Tâche Azure Data Lake Analytics

La tâche Azure Data Lake Analytics permet aux utilisateurs de soumettre des travaux U-SQL au service Azure Data Lake Analytics. [Azure Data Lake Analytics (ADLA)](https://azure.microsoft.com/services/data-lake-analytics/).

La tâche Azure Data Lake Analytics est un composant de [SQL Server Integration Services (SSIS) Feature Pack pour Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

## <a name="configure-the-azure-data-lake-analytics-task"></a>Configurer la tâche Azure Data Lake Analytics

Pour ajouter une tâche Azure Data Lake Analytics à un package, faites-la glisser de la boîte à outils SSIS à la zone de conception. Ensuite, double-cliquez sur la tâche, ou cliquez dessus avec le bouton droit et sélectionnez **Modifier**, pour ouvrir la boîte de dialogue **Éditeur de tâches Azure Data Lake Analytics**. Vous pouvez définir les propriétés par le biais du concepteur SSIS ou par programmation.

## <a name="general-page-configuration"></a>Configuration de la page Général

Sur la page **Général**, configurez la tâche Azure Data Lake Analytics et fournissez le script U-SQL soumis par la tâche. Pour plus d’informations sur le langage U-SQL, voir [Référence du langage U-SQL](https://msdn.microsoft.com/azure/data-lake-analytics/u-sql/u-sql-language-reference).

### <a name="basic-configuration"></a>Configuration de base

- **Nom :** nom de la tâche Azure Data Lake Analytics.
- **Description :** description de la tâche Azure Data Lake Analytics.

### <a name="u-sql-configuration"></a>Configuration U-SQL

La configuration U-SQL comporte deux paramètres : **SourceType** et des options dynamiques qui dépendent de la valeur **SourceType**. 

- **SourceType :** source du script U-SQL. Le script sera soumis à un compte Azure Data Lake Analytics pendant l’exécution du package SSIS. Cette propriété a trois options, listées dans le tableau suivant.

|Valeur|Description|  
|-----------|-----------------|  
|**DirectInput**|Spécifie le script U-SQL par le biais de l’éditeur inline. Sélectionnez cette valeur pour afficher l’option dynamique **USQLStatement**.|  
|**FileConnection**|Spécifie un fichier .usql local contenant le script U-SQL. Sélectionnez cette option pour afficher l’option dynamique **FileConnection**.|  
|**Variable**|Spécifie une variable SSIS contenant le script U-SQL. Sélectionnez cette valeur pour afficher l'option dynamique **SourceVariable**.|

- **Options dynamiques SourceType :** contenu du script pour la requête U-SQL. 

|SourceType|Options dynamiques|  
|-----------|-----------------|  
|**SourceType = DirectInput**|Tapez directement la requête U-SQL à envoyer dans la zone des options, ou cliquez sur le bouton Parcourir (…) pour la taper dans la boîte de dialogue **Entrer une requête U-SQL**.|  
|**SourceType = FileConnection**|Sélectionnez un gestionnaire de connexions de fichiers existant ou cliquez sur <**Nouvelle connexion…**> pour créer une connexion de fichiers. **Article connexe :** [Gestionnaire de connexions de fichiers](../../integration-services/connection-manager/file-connection-manager.md), [Éditeur du gestionnaire de connexions de fichiers](../../integration-services/connection-manager/file-connection-manager-editor.md)|  
|**SourceType = Variable**|Sélectionnez une variable existante ou cliquez sur \<**Nouvelle variable...**> pour en créer une. **Article connexe :** [Variables Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md), [Ajouter une variable](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)|


### <a name="job-configuration"></a>Configuration des travaux
La configuration des travaux spécifie les propriétés de soumission des travaux U-SQL.

- **AzureDataLakeAnalyticsConnection :** compte Azure Data Lake Analytics auquel le script U-SQL sera soumis. Choisissez la connexion dans la liste des gestionnaires de connexions définis. Pour créer une connexion, sélectionnez <**Nouvelle connexion**>. Article connexe : [Gestionnaire de connexions Azure Data Lake Analytics](../../integration-services/connection-manager/azure-data-lake-analytics-connection-manager.md).

- **JobName :** nom du travail U-SQL. 
- **AnalyticsUnits :** nombre d’unités Analytique du travail U-SQL.
- **Priority :** priorité du travail U-SQL. Elle est comprise entre 0 et 1 000 ; plus le nombre est faible, plus la priorité est élevée.
- **RuntimeVersion :** version du runtime Azure Data Lake Analytics du travail U-SQL. Valeur par défaut : « default ». En général, il n’est pas nécessaire de modifier cette propriété.
- **Synchronous :** valeur booléenne indiquant si la tâche attend ou non la fin de l’exécution du travail. Si la valeur est True, la tâche sera marquée comme Succès une fois le travail terminé. Si la valeur est False, la tâche sera marquée comme Succès après la phase de préparation.

|Valeur|Description|
|-----------|-----------------|
|True|Le résultat de la tâche dépend du résultat de l’exécution du travail U-SQL. Réussite du travail --> réussite de la tâche ; échec du travail --> échec de la tâche ; réussite ou échec de la tâche--> fin de la tâche.|
|False|Le résultat de la tâche dépend du résultat de la soumission et de la préparation du travail U-SQL. Réussite de la soumission du travail et de la phase de préparation --> réussite de la tâche ; échec de la soumission du travail ou échec du travail lors de la phase de préparation--> échec de la tâche ; réussite ou échec de la tâche--> fin de la tâche.|

- **TimeOut :** délai d’attente en secondes de l’exécution du travail. Le travail sera annulé et la tâche marquée comme Échec après l’expiration de ce délai d’attente. La propriété TimeOut n’est pas disponible si Synchronous est défini sur False. La propriété TimeOut n’est pas disponible si **Synchronous** est défini sur **False**.

## <a name="parameter-mapping-page-configuration"></a>Configuration de la page Mappage des paramètres

Sur la page **Mappage des paramètres** de la boîte de dialogue **Éditeur de tâches Azure Data Lake Analytics**, mappez les variables avec les paramètres (variables U-SQL) dans le script U-SQL.

- **Nom de variable :** après avoir ajouté un mappage de paramètres en cliquant sur **Ajouter**, sélectionnez une variable système ou une variable définie par l’utilisateur dans la liste ou cliquez sur \<**Nouvelle variable…**> pour ajouter une nouvelle variable au moyen de la boîte de dialogue **Ajouter une variable**. **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md)  

- **Nom du paramètre :** nom de paramètre/variable dans le script U-SQL. Le nom de paramètre doit commencer par le signe @, comme @Param1. 

Voici un exemple montrant comment passer des paramètres au script U-SQL.

**Exemple de script U-SQL**
```
@searchlog =
    EXTRACT UserId          int,
            Start           DateTime,
            Region          string,
            Query           string,
            Duration        int,
            Urls            string,
            ClickedUrls     string
    FROM @in
    USING Extractors.Tsv(nullEscape:"#NULL#");

@rs1 =
    SELECT Start, Region, Duration
    FROM @searchlog
WHERE Region == "en-gb";

@rs1 =
    SELECT Start, Region, Duration
    FROM @rs1
    WHERE Start <= DateTime.Parse("2012/02/19");

OUTPUT @rs1   
    TO @out
      USING Outputters.Tsv(quoting:false, dateTimeFormat:null);
```

Dans l’exemple de script ci-dessus, les chemins d’accès d’entrée et de sortie sont définis dans les paramètres **@in** et **@out**. Les valeurs des paramètres **@in** et **@out** dans le script U-SQL sont passées dynamiquement par la configuration du mappage des paramètres.

|Nom de la variable|Nom du paramètre|
|-------------|--------------|
|User: Variable1|@in|
|User: Variable2|@out| 

## <a name="expression-page-configuration"></a>Configuration de la page Expression

Toutes les propriétés de configuration de la page Général peuvent être affectées comme expression de propriété pour permettre la mise à jour dynamique de la propriété à l’exécution. **Rubriques connexes :** [Utiliser des expressions de propriété dans des packages](../../integration-services/expressions/use-property-expressions-in-packages.md)

## <a name="see-also"></a> Voir aussi
- [Gestionnaire de connexions Azure Data Lake Analytics](../../integration-services/connection-manager/azure-data-lake-analytics-connection-manager.md)
- [Tâche du système de fichiers Azure Data Lake Store](../../integration-services/control-flow/azure-data-lake-store-file-system-task.md)
- [Gestionnaire de connexions Azure Data Lake Store](../../integration-services/connection-manager/azure-data-lake-store-connection-manager.md)

