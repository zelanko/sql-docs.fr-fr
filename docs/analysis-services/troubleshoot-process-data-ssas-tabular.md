---
title: "D&#233;panner le traitement des donn&#233;es (SSAS Tabulaire) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 678f523c-e181-4456-9a54-7b7bf044b8d2
caps.latest.revision: 12
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 12
---
# D&#233;panner le traitement des donn&#233;es (SSAS Tabulaire)
  Cette rubrique fournit des informations à propos du traitement (actualisation) des données de modèle lors de la création d'un modèle à l'aide de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Cette rubrique ne fournit pas d'informations sur le traitement des données dans les modèles qui ont été déployés vers une instance de serveur Analysis Services. Pour plus d’informations sur le traitement des données dans un modèle déployé, consultez [Tâches d’administration à l’aide de scripts dans Analysis Services](../analysis-services/instances/script-administrative-tasks-in-analysis-services.md).  
  
 Sections de cette rubrique :  
  
-   [Fonctionnement du traitement des données](#bkmk_how_df_works)  
  
-   [Impact du traitement des données](#bkmk_impact_of_df)  
  
-   [Détermination de la source des données](#bkmk_det_source)  
  
-   [Détermination de la date de la dernière actualisation des données](#bkmk_det_last_ref)  
  
-   [Restrictions sur les sources de données actualisables](#bkmk_restrictions)  
  
-   [Restrictions sur les modifications possibles d'une source de données](#bkmk_rest_changes)  
  
##  <a name="bkmk_how_df_works"></a> Fonctionnement du traitement des données  
 Lorsque vous traitez des données, les données contenues dans le générateur de modèles sont remplacées par de nouvelles données. Vous ne pouvez pas simplement importer de nouvelles lignes de données ou uniquement les données modifiées. Le générateur de modèles n'effectue pas de suivi des lignes qui ont été ajoutées précédemment.  
  
 Le traitement des données a lieu comme une transaction. Cela signifie qu'une fois que vous avez commencé la mise à jour des données, la mise à jour complète peut échouer ou réussir ; vous n'obtiendrez jamais des données partiellement correctes.  
  
 Le traitement manuel des données, que vous initiez à partir de [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], est géré par l'instance locale en mémoire d'Analysis Services. L’opération de traitement des données peut donc affecter les performances d’autres tâches sur votre ordinateur. Toutefois, si vous planifiez le processus automatique des données dans un modèle déployé à l’aide d’un script, l’instance d’Analysis Services gère l’importation et son minutage.  
  
##  <a name="bkmk_impact_of_df"></a> Impact du traitement des données  
 Un traitement des données déclenche généralement un recalcul des données.  Le traitement des données implique l'obtention des données les plus récentes à partir des sources externes ; un recalcul correspond à la mise à jour des résultats de toutes les formules qui utilisent des données modifiées. Une opération de traitement déclenche généralement un recalcul.  
  
 Par conséquent, vous devez toujours penser à l'impact potentiel d'une modification des sources de données ou d'un traitement des données obtenues de la source de données et prendre en compte les conséquences éventuelles avant d'agir :  
  
-   Certaines parties des données du modèle peuvent être rompues suite à des modifications apportées dans la source de données. Si certaines colonnes ne peuvent pas être récupérées à partir de la source de données (par exemple, si elles ont été supprimées ou modifiées), le traitement échoue et vous devez mettre à jour les mappages entre les données source et les données du modèle. Pour plus d’informations, consultez [Modifier une connexion à une source de données existante &#40;SSAS Tabulaire&#41;](../analysis-services/tabular-models/edit-an-existing-data-source-connection-ssas-tabular.md).  
  
-   Une fois le traitement terminé, certaines colonnes peuvent être signalées comme contenant une erreur. Cela peut se produire si la formule DAX dans la colonne utilise des données qui n'étaient plus disponibles lors du traitement, si le type de données d'une colonne a changé ou si une valeur non valide a été ajoutée dans les données externes. Pour résoudre ce problème, vous pouvez modifier la formule ou supprimer la colonne si elle est basée sur des données qui ne sont plus disponibles.  
  
-   Les formules qui utilisent les données mises à jour doivent être recalculées. Selon la taille du modèle, cette opération peut être longue.  
  
-   Si votre modèle contient plusieurs sources de données, vous devrez peut-être traiter le modèle entier (Traiter tout) même si une seule source de données externe a changé. Par exemple, si vous créez des mesures qui reposent sur des colonnes calculées et que ces dernières utilisent des valeurs provenant d'autres colonnes calculées, le générateur de modèles analyse d'abord les dépendances, puis traite la chaîne entière d'objets associés dans l'ordre. Selon la complexité des dépendances, cette opération peut être longue.  
  
-   Lorsque vous modifiez un filtre, le modèle entier doit être recalculé.  
  
##  <a name="bkmk_det_source"></a> Détermination de la source des données  
 Si vous n'êtes pas sûr de la provenance des données dans votre modèle, vous pouvez utiliser les outils de la fenêtre [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] pour obtenir ces informations, notamment le nom du fichier source et son chemin d'accès.  
  
#### Pour rechercher la source de données existantes  
  
1.  Dans le générateur de modèles, sélectionnez la table qui contient les données pour lesquelles vous souhaitez connaître la source.  
  
2.  Cliquez sur le menu **Table** , puis sur **Propriétés de la table**.  
  
3.  Dans la boîte de dialogue **Modifier les propriétés de la table** , notez la valeur répertoriée pour **Nom de la connexion**.  
  
4.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], dans le menu **Modèle** , cliquez sur **Connexions existantes**.  
  
5.  Dans la boîte de dialogue **Connexions existantes** , sélectionnez la source de données portant le nom que vous avez trouvé à l'étape 3, puis cliquez sur **Modifier**.  
  
6.  Dans la boîte de dialogue **Modifier les connexions** , consultez les informations de connexion, telles que le nom de la base de données, le chemin d'accès au fichier ou le chemin d'accès au rapport.  
  
##  <a name="bkmk_det_last_ref"></a> Détermination de la date de la dernière actualisation des données  
 Vous pouvez utiliser les propriétés de table pour déterminer quand les données ont été actualisées pour la dernière fois.  
  
#### Pour rechercher la date et l'heure du dernier traitement d'une table  
  
1.  Dans le générateur de modèles, sélectionnez la table qui contient les données pour lesquelles vous souhaitez connaître la dernière date d'actualisation.  
  
2.  Cliquez sur le menu **Table** , puis sur **Propriétés de la table**.  
  
3.  Dans la boîte de dialogue **Modifier les propriétés de la table** , la zone **Dernière actualisation** indique la dernière date à laquelle la table a été actualisée.  
  
##  <a name="bkmk_restrictions"></a> Restrictions sur les sources de données actualisables  
 Certaines restrictions s'appliquent aux sources de données qui peuvent être automatiquement traitées à partir d'un modèle déployé sur une instance Analysis Services. Veillez à ne sélectionner que des sources de données qui répondent aux critères suivants :  
  
-   La source de données doit être disponible au moment où s'effectue le traitement des données et disponible à l'emplacement indiqué. Si la source de données d'origine se trouve sur un lecteur de disque local de l'utilisateur qui a créé le modèle, vous devez soit exclure cette source de données de l'opération de traitement, soit trouver un moyen de publier cette source de données à un emplacement accessible via une connexion réseau. Si vous déplacez une source de données vers un emplacement réseau, veillez à ouvrir le modèle dans le générateur de modèles et répétez les étapes de récupération des données. Ces opérations sont nécessaires pour rétablir les informations de connexion stockées dans les propriétés de connexion de la source de données.  
  
-   L'accès à la source de données doit se faire au moyen des informations d'identification incorporées dans la connexion de la source de données. Les informations d'identification incorporées sont créées dans la connexion de la source de données lorsque vous vous connectez à la source de données externe.  
  
-   Le traitement des données doit réussir pour toutes les sources de données que vous spécifiez. Si ce n'est pas le cas, les données traitées sont ignorées, et vous vous retrouvez avec la dernière version enregistrée du modèle. Excluez toutes les sources de données pour lesquelles vous avez un doute.  
  
-   Le traitement des données ne doit pas invalider d'autres données de votre modèle. Lorsque vous traitez un sous-ensemble de vos données, il est essentiel que vous compreniez si le modèle est toujours valide une fois les données les plus récentes agrégées avec les données statiques qui ne s'inscrivent pas sur la même période. En tant que générateur de modèles, il vous appartient de connaître les dépendances de vos données et de faire en sorte que le traitement des données soit approprié pour le modèle lui-même.  
  
     L'accès à une source de données externe s'effectue au moyen d'une chaîne de connexion incorporée, d'une URL ou d'un chemin d'accès UNC que vous avez spécifié lorsque vous avez importé les données d'origine dans le modèle à l'aide de l'Assistant Importation de table. Les informations de connexion d'origine stockées dans la connexion de la source de données sont réutilisées pour les opérations d'actualisation des données suivantes. Il n'existe pas d'autres informations de connexion qui puissent être créées et gérées à des fins de traitement des données ; seules les informations de connexion existantes sont utilisées.  
  
##  <a name="bkmk_rest_changes"></a> Restrictions sur les modifications possibles d'une source de données  
 Il existe des restrictions sur les modifications que vous pouvez apporter à une source de données :  
  
-   Les types de données d'une colonne peuvent être uniquement modifiés par un type de données compatible. Par exemple, si les données de la colonne incluent des nombres décimaux, vous ne pouvez pas modifier le type de données par un entier. Toutefois, vous pouvez changer les données numériques en texte. Pour plus d’informations sur les types de données, consultez [Types de données pris en charge &#40;SSAS Tabulaire&#41;](../analysis-services/tabular-models/data-types-supported-ssas-tabular.md).  
  
-   Vous ne pouvez pas effectuer une multi-sélection de colonnes dans des tables différentes et modifier les propriétés des colonnes. Vous pouvez travailler avec une seule table ou vue à la fois.  
  
## Voir aussi  
 [Traiter manuellement les données &#40;SSAS Tabulaire&#41;](../analysis-services/tabular-models/manually-process-data-ssas-tabular.md)   
 [Modifier une connexion à une source de données existante &#40;SSAS Tabulaire&#41;](../analysis-services/tabular-models/edit-an-existing-data-source-connection-ssas-tabular.md)  
  
  