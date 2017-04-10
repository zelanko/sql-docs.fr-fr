---
title: "Destination OLE&#160;DB | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.oledbdest.f1"
helpviewer_keywords: 
  - "mode d'accès aux données à chargement rapide [Integration Services]"
  - "Destination OLE DB [Integration Services]"
  - "options de chargement rapide [Integration Services]"
  - "options de chargement rapide [Integration Services]"
  - "destinations [Integration Services], OLE DB"
  - "mode d'accès aux données à chargement rapide [Integration Services]"
  - "insertion de données"
ms.assetid: 873a2fa0-2a02-41fc-a80a-ec9767f36a8a
caps.latest.revision: 79
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 79
---
# Destination OLE&#160;DB
  La destination OLE DB charge des données dans différentes bases de données compatibles OLE DB à l'aide d'une table ou d'une vue de base de données ou d'une commande SQL. Par exemple, la source OLE DB peut charger des données dans des tables de bases de données [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  Si la source de données est [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Excel 2007, la source de données requiert un gestionnaire de connexions différent des versions antérieures d'Excel. Pour plus d’informations, consultez [Établir une connexion à un classeur Excel](../../integration-services/connection-manager/connect-to-an-excel-workbook.md).  
  
 La destination OLE DB propose cinq modes d'accès différents pour charger les données :  
  
-   Une table ou une vue. Vous pouvez indiquer une table ou une vue existante, ou créer une table ;  
  
-   une table ou une vue et des options de chargement rapide. Vous pouvez indiquer une table existante ou en créer une ;  
  
-   Une table ou une vue spécifiée dans une variable.  
  
-   une table ou une vue spécifiée dans une variable et des options de chargement rapide ;  
  
-   Les résultats d'une instruction SQL.  
  
> [!NOTE]  
>  La destination OLE DB ne prend pas en charge les paramètres. Si vous devez exécuter une instruction INSERT paramétrable, envisagez d'utiliser la transformation de commande OLE DB. Pour plus d’informations, consultez [OLE DB Command Transformation](../../integration-services/data-flow/transformations/ole-db-command-transformation.md).  
  
 Lorsque la destination OLE DB charge des données qui utilisent un jeu de caractères codés sur deux octets (DBCS), les données risquent d'être endommagées si le mode d'accès aux données n'utilise pas l'option de chargement rapide et si le gestionnaire de connexions OLE DB utilise le fournisseur [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB pour SQL Server [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQLOLEDB). Pour garantir l’intégrité des données DBCS, vous devez configurer le gestionnaire de connexions OLE DB pour utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ou l’un des modes d’accès avec chargement rapide : **Table ou vue - chargement rapide** ou **Variable de nom de table ou de vue - chargement rapide**. Ces deux options sont disponibles dans la boîte de dialogue **Éditeur de destination OLE DB** . Quand vous programmez le modèle d’objet [!INCLUDE[ssIS](../../includes/ssis-md.md)], vous devez définir la propriété AccessMode sur **OpenRowset à l’aide de FastLoad** ou **OpenRowset à l’aide de FastLoad à partir de Variable**.  
  
> [!NOTE]  
>  Si vous utilisez la boîte de dialogue **Éditeur de destination OLE DB** dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] pour créer la table de destination dans laquelle la destination OLE DB insère des données, vous devrez peut-être sélectionner la table que vous venez de créer manuellement. La sélection manuelle est nécessaire lorsqu'un fournisseur OLE DB tel que le fournisseur OLE DB pour DB2, ajoute manuellement des identificateurs de schéma au nom de la table.  
  
> [!NOTE]  
>  L'instruction CREATE TABLE que la boîte de dialogue **Éditeur de destination OLE DB** génère peut nécessiter une modification selon le type de destination. Par exemple, certaines destinations ne prennent pas en charge les types de données que l'instruction CREATE TABLE utilise.  
  
 Cette destination utilise un gestionnaire de connexions OLE DB pour se connecter à une source de données et le gestionnaire de connexions indique le fournisseur OLE DB à utiliser. Pour plus d’informations, consultez [OLE DB Connection Manager](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
 Un projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contient également l'objet de source de données à partir duquel vous pouvez créer un gestionnaire de connexions OLE DB afin de rendre les sources de données et les vues de sources de données disponibles pour la destination OLE DB.  
  
 Une destination OLE DB inclut des mappages entre les colonnes d'entrée et les colonnes de la source de données de destination. Vous n'avez pas besoin de mapper les colonnes d'entrée à toutes les colonnes de destination, mais en fonction des propriétés des colonnes de destination, des erreurs peuvent se produire si aucune colonne d'entrée n'est mappée aux colonnes de destination. Par exemple, si une colonne de destination n'autorise pas les valeurs null, une colonne d'entrée doit être mappée à cette colonne. Par ailleurs, les types de données des colonnes mappées doivent être compatibles. Par exemple, vous ne pouvez pas mapper une colonne d'entrée avec un type de données string à une colonne de destination avec un type de données numeric.  
  
 La destination OLE DB comporte une entrée normale et une sortie d'erreur.  
  
 Pour plus d'informations sur les types de données, consultez [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## Options de chargement rapide  
 Si la destination OLE DB utilise un mode d’accès aux données par chargement rapide, vous pouvez spécifier les options de chargement rapide dans l’interface utilisateur, **Éditeur de destination OLE DB**, pour la destination :  
  
-   Conserver les valeurs d'identité du fichier de données importé ou utiliser les valeurs uniques affectées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Conserver une valeur null pendant l'opération de chargement en masse.  
  
-   Vérifier les contraintes sur la table ou la vue cible au cours de l'opération d'importation en masse.  
  
-   Acquisition d'un verrou au niveau de la table pour la durée de l'opération de chargement en masse.  
  
-   Spécifier le nombre de lignes dans le traitement et la taille de validation.  
  
 Certaines options de chargement rapide sont stockées dans des propriétés spécifiques de la destination OLE DB. Par exemple, FastLoadKeepIdentity spécifie s’il convient de conserver des valeurs d’identification, FastLoadKeepNulls précise s’il faut conserver des valeurs NULL et FastLoadMaxInsertCommitSize spécifie le nombre de lignes à valider en tant que traitement. D’autres options de chargement rapide sont stockées dans une liste séparée par des virgules dans la propriété FastLoadOptions. Si la destination OLE DB utilise toutes les options de chargement rapide qui sont stockées dans FastLoadOptions et répertoriées dans la boîte de dialogue **Éditeur de destination OLE DB**, la propriété prend la valeur **TABLOCK, CHECK_CONSTRAINTS, ROWS_PER_BATCH=1000**. La valeur 1 000 indique que la destination est configurée pour utiliser des traitements de 1 000 lignes.  
  
> [!NOTE]  
>  Tout échec de contrainte à la destination entraîne l’échec de la totalité du lot de lignes définies par FastLoadMaxInsertCommitSize.  
  
 Outre les options de chargement rapide dévoilées dans la boîte de dialogue **Éditeur de destination OLE DB**, vous pouvez configurer la destination OLE DB afin d’utiliser les options de chargement en masse suivantes en tapant les options dans la propriété FastLoadOptions, dans la boîte de dialogue **Éditeur avancé**.  
  
|Option de chargement rapide|Description|  
|----------------------|-----------------|  
|KILOBYTES_PER_BATCH|Indique la taille à insérer en kilo-octets. L’option a la forme **KILOBYTES_PER_BATCH** = \<valeur entière positive**>**.|  
|FIRE_TRIGGERS|Spécifie si des déclencheurs sont activés sur la table d'insertion. L’option a la forme **FIRE_TRIGGERS**. La présence de l'option indique que des déclencheurs sont activés.|  
|ORDER|Spécifie comment les données d'entrée sont triées. L’option a la forme ORDER \<nom de colonne> ASC&#124;DESC. Il n'y a pas de limite quant au nombre de colonnes indiquées et la spécification de l'ordre de tri est facultative. Si l'ordre de tri est omis, l'opération d'insertion part du principe que les données ne sont pas triées.<br /><br /> Remarque : les performances peuvent être améliorées si vous utilisez l’option ORDER pour trier les données d’entrée selon l’index cluster de la table.|  
  
 Les mots clés [!INCLUDE[tsql](../../includes/tsql-md.md)] sont traditionnellement tapés en majuscules, mais ils ne tiennent pas compte de la casse.  
  
 Pour en savoir plus sur les options de chargement rapide, consultez [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md).  
  
## Résolution des problèmes liés à la destination OLE DB  
 Vous pouvez consigner les appels que la destination OLE DB effectue vers des fournisseurs de données externes. Cette fonctionnalité de journalisation permet de résoudre des problèmes liés à l'enregistrement de données vers des sources de données externes que réalise la destination OLE DB. Pour consigner les appels que la destination OLE DB effectue vers des fournisseurs de données externes, activez la journalisation de package et sélectionnez l'événement **Diagnostic** au niveau du package. Pour plus d’informations, consultez [Outils de dépannage pour l’exécution des packages](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
## Configuration de la destination OLE DB  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur de destination OLE DB** , cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur de destination OLE DB &#40;page Gestionnaire de connexions&#41;](../../integration-services/data-flow/ole-db-destination-editor-connection-manager-page.md)  
  
-   [Éditeur de destination OLE DB &#40;page Mappages&#41;](../../integration-services/data-flow/ole-db-destination-editor-mappings-page.md)  
  
-   [Éditeur de destination OLE DB &#40;page Sortie d’erreur&#41;](../../integration-services/data-flow/ole-db-destination-editor-error-output-page.md)  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programme. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programme, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../Topic/Common%20Properties.md)  
  
-   [Propriétés personnalisées OLE DB](../../integration-services/data-flow/ole-db-custom-properties.md)  
  
 Pour plus d'informations sur la définition des propriétés, cliquez sur l'une des rubriques suivantes :  
  
-   [Charger des données à l'aide de la destination OLE DB](../../integration-services/data-flow/load-data-by-using-the-ole-db-destination.md)  
  
-   [Définir les propriétés d'un composant de flux de données](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
## Contenu connexe  
 [Source OLE DB](../../integration-services/data-flow/ole-db-source.md)  
  
 [Variables Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md)  
  
 [Flux de données](../../integration-services/data-flow/data-flow.md)  
  
  