---
title: Scénarios de déploiement DirectQuery (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 2aaf5cb8-294b-4031-94b3-fe605d7fc4c7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 679658c7ffdc00a90cb485bb9f1892ddffde7775
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62731665"
---
# <a name="directquery-deployment-scenarios-ssas-tabular"></a>Scénarios de déploiement DirectQuery (SSAS Tabulaire)
  Cette rubrique fournit une procédure pas-à-pas présentant le processus de conception et de déploiement des modèles DirectQuery. Vous pouvez configurer DirectQuery pour utiliser des données relationnelles uniquement (DirectQuery uniquement), ou vous pouvez configurer le modèle pour basculer entre l'utilisation de données en mémoire cache uniquement ou de données relationnelles uniquement (mode hybride). Cette rubrique présente le processus d'implémentation pour les deux modes, et décrit les différences possibles dans les résultats de la requête selon le mode et la configuration de la sécurité.  
  
 [Conception et les étapes de déploiement](#bkmk_DQProcedure)  
  
 [Comparaison des Configurations DirectQuery](#bkmk_Configurations)  
  
##  <a name="bkmk_DQProcedure"></a> Conception et les étapes de déploiement  
 **Étape 1. Créer la solution**  
  
 Quel que soit le mode que vous allez utiliser, vous devez vérifier les informations qui décrivent les limitations applicables aux données pouvant être utilisées dans les modèles DirectQuery. Par exemple, toutes les données utilisées dans votre modèle et vos rapports doivent provenir d'une même base de données SQL Server. Pour plus d’informations, consultez [Mode DirectQuery &#40;SSAS Tabulaire&#41;](tabular-models/directquery-mode-ssas-tabular.md).  
  
 En outre, examinez les limitations applicables aux mesures et aux colonnes calculées, et déterminez si les formules que vous envisagez d'utiliser sont compatibles avec le mode DirectQuery. Vous devrez peut-être supprimer ou modifier les éléments suivants :  
  
-   Les colonnes calculées ne sont pas prises en charge.  
  
-   Les données copiées-collées ne peuvent pas être utilisées. Si vous importez un modèle PowerPivot pour accélérer votre solution, assurez-vous de supprimer les tables liées avant d'importer la solution, car ces données ne peuvent pas être supprimées ultérieurement et bloqueront la validation de DirectQuery.  
  
 **Étape 2. Activer le mode DirectQuery dans le Générateur de modèles**  
  
 Par défaut, DirectQuery est désactivé. Par conséquent, vous devez configurer l'environnement de conception de manière à prendre en charge le mode DirectQuery.  
  
 Avec le bouton droit le **Model.bim** nœud dans l’Explorateur de solutions et attribuez à la propriété **DirectQuery Mode**à `On`.  
  
 Vous pouvez activer DirectQuery à tout moment ; cependant, pour vous assurer de ne pas créer de colonnes ou formules incompatibles avec le mode DirectQuery, nous vous recommandons d'activer le mode DirectQuery dès le départ.  
  
 Initialement, même les modèles DirectQuery sont toujours créés en mémoire. Le mode de requête par défaut pour la base de données d'espace de travail est également défini sur **DirectQuery avec InMemory**. Ce mode de travail hybride vous permet d'utiliser le cache de données importées pour améliorer les performances lors du processus de conception de modèle, tout en validant le modèle en fonction des spécifications DirectQuery.  
  
 **Étape 3. Résoudre les erreurs de validation**  
  
 Si vous obtenez des erreurs de validation lorsque vous activez DirectQuery, ou lorsque vous ajoutez de nouvelles données ou formules, ouvrez la **Liste d'erreurs**Visual Studio, puis effectuez les actions requises.  
  
-   Modifiez tous les paramètres de propriétés requis pour le mode DirectQuery, comme décrit dans les messages d'erreur.  
  
-   Supprimez les colonnes calculées. Si vous avez besoin d’une colonne calculée pour une mesure donnée, vous pouvez toujours créer la colonne à l’aide de la [Concepteur de requêtes relationnelles &#40;SSAS&#41; ](relational-query-designer-ssas.md) fourni dans l’Assistant Importation de Table.  
  
-   Modifiez ou supprimez les formules qui ne sont pas compatibles avec le mode DirectQuery. Si vous avez besoin d'une fonction particulière pour un calcul, réfléchissez aux méthodes pouvant fournir un équivalent à l'aide de Transact-SQL.  
  
-   Ajoutez des données si nécessaire.  Si votre modèle utilisait précédemment des données copiées-collées ou des données des fournisseurs autres que SQL Server, vous pouvez créer des vues et colonnes dérivées avec la connexion existante, ou utiliser des requêtes distribuées.  Toutes les données utilisées dans un modèle DirectQuery doivent être accessibles par le biais d'une seule source de données SQL Server.  
  
 **Étape 4. Définissez la méthode recommandée pour répondre aux requêtes sur le modèle**  
  
|||  
|-|-|  
|**DirectQuery uniquement**|Affectez à la propriété la valeur **DirectQuery**.|  
|**Mode hybride**|Définissez la propriété sur **InMemory avec DirectQuery** ou à **DirectQuery avec InMemory**.<br /><br /> Vous pouvez modifier cette valeur ultérieurement pour utiliser une préférence différente.<br /><br /> Notez que les clients peuvent remplacer la méthode recommandée dans la chaîne de connexion.|  
  
 **Étape 5. Spécifiez la partition DirectQuery**  
  
|||  
|-|-|  
|**DirectQuery uniquement**|Facultatif. Un modèle DirectQuery uniquement n'a pas besoin de partition.<br /><br /> Toutefois, si vous avez créé des partitions dans le modèle pendant la phase de conception, souvenez-vous qu'une seule partition peut être utilisée en tant que source de données. Par défaut, la première partition que vous avez créée est utilisée en tant que partition DirectQuery.<br /><br /> Pour vous assurer que toutes les données requises par le modèle sont disponibles dans la partition DirectQuery, choisissez une partition DirectQuery et modifiez l'instruction SQL de manière à obtenir l'ensemble de données complet.|  
|**Mode hybride**|Si une table de votre modèle comporte plusieurs partitions, vous devez choisir une seule partition en tant que *partition DirectQuery*. Si vous n'affectez pas de partition, par défaut, la première partition qui a été créée sera utilisée en tant que partition DirectQuery.<br /><br /> Définissez les options de traitement sur toutes les partitions, à l'exception de DirectQuery. En général, la partition DirectQuery n'est jamais traitée, car les données sont transmises depuis la source relationnelle.<br /><br /> Pour plus d’informations, consultez [Partitions et DirectQuery Mode &#40;tabulaire SSAS&#41;](tabular-models/define-partitions-in-directquery-models-ssas-tabular.md).|  
  
 **Étape 6. Configurer l’emprunt d’identité**  
  
 L'emprunt d'identité n'est pris en charge que pour les modèles DirectQuery. L'option d'emprunt d'identité, **Paramètres d'emprunt d'identité**, définit les informations d'identification utilisées lors de l'affichage des données de la source de données SQL Server spécifiée.  
  
|||  
|-|-|  
|**DirectQuery uniquement**|Pour la propriété  **Paramètres d'emprunt d'identité** , spécifiez le compte qui sera utilisé pour se connecter à la source de données SQL Server.<br /><br /> Si vous utilisez la valeur **ImpersonateCurrentUser**, l'instance d' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] qui héberge le modèle passe les informations d'identification de l'utilisateur actuel du modèle à la base de données SQL Server.|  
|**Mode hybride**|Pour la propriété **Paramètres d'emprunt d'identité** , spécifiez le compte qui sera utilisé pour accéder aux données contenues dans la source de données SQL Server.<br /><br /> Ce paramètre n'affecte pas les informations d'identification utilisées pour traiter le cache utilisé par le modèle.|  
  
 **Étape 7. Déployer le modèle**  
  
 Lorsque vous êtes prêt à déployer le modèle, ouvrez le **projet** menu de Visual Studio, puis sélectionnez **propriétés**. Affectez à la propriété **QueryMode** l'une des valeurs décrites dans le tableau suivant :  
  
 Pour plus d’informations, consultez [déployer à partir de SQL Server Data Tools &#40;tabulaire SSAS&#41;](tabular-models/deploy-from-sql-server-data-tools-ssas-tabular.md).  
  
|||  
|-|-|  
|**DirectQuery uniquement**|**DirectQueryOnly**<br /><br /> Étant donné que vous avez spécifié DirectQuery uniquement, les métadonnées du modèle sont déployées sur le serveur, mais le modèle n'est pas traité.<br /><br /> Notez que le cache utilisé par la base de données d'espace de travail n'est pas supprimé automatiquement. Si vous souhaitez vous assurer que les utilisateurs ne peuvent pas voir les données en cache, vous pouvez effacer le cache au moment de la conception. Pour plus d’informations, consultez [effacer les Caches de Services d’analyse](instances/clear-the-analysis-services-caches.md).|  
|**Mode hybride**|**DirectQuery avec In-Memory**<br /><br /> **In-Memory avec DirectQuery**<br /><br /> Ces deux valeurs vous permettent d'utiliser le cache ou la source de données relationnelle selon les besoins. L'ordre définit quelle source de données est utilisée par défaut lors de la réponse aux requêtes sur le modèle.<br /><br /> En mode hybride, le cache doit être traité en même temps que le déploiement des métadonnées du modèle sur le serveur.<br /><br /> Vous pouvez modifier ce paramètre après le déploiement.|  
  
 **Étape 8. Vérifiez le modèle déployé**  
  
 Dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], ouvrez l'instance d' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans laquelle vous avez déployé le modèle. Cliquez avec le bouton droit sur le nom de la base de données, puis sélectionnez **Propriétés**.  
  
-   La propriété, **DirectQueryMode**, a été définie lorsque vous avez défini les propriétés de déploiement.  
  
-   La propriété, **Informations d'emprunt d'identité de source de données**, a été définie lorsque vous avez défini les options d'emprunt d'identité. Pour plus d’informations, consultez [Définir les options d’emprunt d’identité &#40;SSAS - Multidimensionnel&#41;](multidimensional-models/set-impersonation-options-ssas-multidimensional.md).  
  
-   Vous pouvez modifier ces propriétés à tout moment après que le modèle a été déployé.  
  
##  <a name="bkmk_Configurations"></a> Comparaison des Options DirectQuery  
 **DirectQuery uniquement**  
 Cette option est recommandée lorsque vous voulez garantir une seule source de données, ou si vos données sont trop volumineuses pour tenir en mémoire. Si vous utilisez une source de données relationnelle très volumineuse, lors de la conception, vous pouvez créer le modèle à l'aide d'un sous-ensemble des données. Lorsque vous déployez le modèle en mode DirectQuery uniquement, vous pouvez modifier la définition de la source de données de manière à inclure toutes les données requises.  
  
 Cette option est également recommandée si vous souhaitez utiliser la sécurité fournie par la source de données relationnelle pour contrôler l'accès utilisateur aux données. Avec les modèles tabulaires mis en cache, vous pouvez également utiliser des rôles [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] pour contrôler l'accès aux données, mais les données stockées dans le cache doivent également être sécurisées. Vous devez toujours utiliser cette option si votre contexte de sécurité nécessite que les données ne soient jamais mises en cache.  
  
 Le tableau suivant décrit les résultats de déploiement possibles pour le mode DirectQuery uniquement :  
  
|||  
|-|-|  
|**DirectQuery sans cache**|Aucune donnée n'est chargée dans le cache. Le modèle ne peut jamais être traité.<br /><br /> Le modèle peut être interrogé à l'aide des clients qui prennent en charge les requêtes DAX. Les résultats de la requête sont toujours retournés à partir de la source de données d'origine.<br /><br /> **DirectQueryMode** = `On`<br /><br /> **QueryMode** = **DirectQuery**|  
|**DirectQuery avec des requêtes sur le cache uniquement**|Échec de déploiement. Cette configuration n'est pas prise en charge.<br /><br /> **DirectQueryMode** = `On`<br /><br /> **QueryMode** = **In-Memory**|  
  
 **Mode hybride**  
 Le déploiement de votre modèle en mode hybride présente de nombreux avantages : vous pouvez obtenir des données à jour de la source de données SQL Server si nécessaire, mais en conservant le cache vous pouvez utiliser des données en mémoire pour améliorer les performances lors de la conception des rapports ou du test du modèle.  
  
 Le mode hybride de DirectQuery est également utile si votre modèle est très volumineux. Pour éviter que les utilisateurs obtiennent des données obsolètes ou ne puissent pas accéder au modèle pendant le traitement du cache, vous pouvez basculer le modèle en mode DirectQuery alors que le traitement est en cours. Les utilisateurs peuvent rencontrer une légère baisse des performances, mais ils obtiennent des données directement à partir du magasin relationnel, ce qui garantit que les résultats sont à jour.  
  
 Le tableau suivant compare les résultats de déploiement dans chacune des combinaisons d'options du mode DirectQuery.  
  
|||  
|-|-|  
|**Mode hybride avec cache par défaut**|Le modèle peut être traité et les données peuvent être chargées dans le cache. Les requêtes utilisent le cache par défaut.  Si un client souhaite utiliser la source DirectQuery, un paramètre doit être inséré dans la chaîne de connexion.<br /><br /> **DirectQueryMode** = `On`<br /><br /> **QueryMode** = **In-Memory with DirectQuery**|  
|**Mode hybride avec DirectQuery par défaut**|Le modèle est traité et les données peuvent être chargées dans le cache. Toutefois, les requêtes utilisent DirectQuery par défaut. Si un client souhaite utiliser les données en cache, un paramètre doit être inséré dans la chaîne de connexion. Si les tables du modèle sont partitionnées, la valeur de la partition principale du cache est également **InMemory avec DirectQuery**.<br /><br /> **DirectQueryMode** = `On`<br /><br /> **QueryMode** = **DirectQuery avec InMemory**|  
  
## <a name="see-also"></a>Voir aussi  
 [Mode DirectQuery &#40;SSAS Tabulaire&#41;](tabular-models/directquery-mode-ssas-tabular.md)   
 [Accès aux données de modèle tabulaire](tabular-models/tabular-model-data-access.md)  
  
  
