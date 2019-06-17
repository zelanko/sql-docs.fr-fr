---
title: L’emprunt d’identité (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: fcc79e96-182a-45e9-8ae2-aeb440e9bedd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 81e8f9ae90db3c7613ccb99039d70d9a28c5a113
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66067060"
---
# <a name="impersonation-ssas-tabular"></a>Emprunt d'identité (SSAS Tabulaire)
  Cette rubrique explique aux créateurs de modèles tabulaires comment les informations d'identification d'ouverture de session sont utilisées par Analysis Services lors de la connexion à une source de données pour importer et traiter (actualiser) des données.  
  
 Cet article contient les sections suivantes :  
  
-   [Avantages](#bkmk_how_imper)  
  
-   [Options](#bkmk_imp_info_options)  
  
-   [Sécurité](#bkmk_impers_sec)  
  
-   [Emprunt d'identité lors de l'importation d'un modèle](#bkmk_imp_newmodel)  
  
-   [Configuration de l'emprunt d'identité](#bkmk_conf_imp_info)  
  
##  <a name="bkmk_how_imper"></a> Avantages  
 L'*emprunt d'identité* est la capacité d'une application serveur, telle qu'Analysis Services, d'assumer l'identité d'une application cliente. Analysis Services s'exécute en utilisant un compte de service ; toutefois, lorsque le serveur établit une connexion à une source de données, il utilise l'emprunt d'identité afin d'effectuer les vérifications d'accès pour l'importation et le traitement des données.  
  
 Les informations d'identification utilisées pour l'emprunt d'identité sont différentes des informations d'identification de l'utilisateur actuellement connecté. Les informations d'identification de l'utilisateur connecté sont utilisées pour des opérations côté client spécifiques lors de la création d'un modèle.  
  
 Il est important de comprendre comment les informations d’identification d’emprunt d’identité sont spécifiées et sécurisées ainsi que la différence entre les contextes dans lesquels l’analyseur lexical actuel ouvert une session de l’utilisateur ainsi que lorsque les autres informations d’identification sont utilisées.  
  
 **Présentation des informations d'identification côté serveur**  
  
 Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], les informations d'identification sont spécifiées pour chaque source de données en utilisant la page **Informations d'emprunt d'identité** dans l'Assistant Importation de table ou en modifiant une connexion à la source de données existante dans la boîte de dialogue **Connexions existantes** .  
  
 Lorsque les données sont importées ou traitées, les informations d'identification spécifiées dans la page **Informations d'emprunt d'identité** sont utilisées pour la connexion à la source de données et l'extraction des données. C'est une opération *côté serveur* qui fonctionne dans le contexte d'une application cliente parce que le serveur Analysis Services qui héberge la base de données d'espace de travail se connecte à la source de données et extrait les données.  
  
 Lorsque vous déployez un modèle sur un serveur Analysis Services, si la base de données d'espace de travail est en mémoire lorsque le modèle est déployé, les informations d'identification sont passées au serveur Analysis Services sur lequel le modèle est déployé. À aucun moment les informations d'identification de l'utilisateur sont stockées sur le disque.  
  
 Lorsqu'un modèle déployé traite des données d'une source de données, les informations d'identification d'emprunt d'identité, rendues persistantes dans la base de données en mémoire, sont utilisées pour la connexion à la source de données et l'extraction des données. Étant donné que ce processus est contrôlé par le serveur Analysis Services qui gère la base de données model, c'est encore une opération côté serveur.  
  
 **Présentation des informations d'identification côté client**  
  
 Lors de la création d'un modèle ou de l'ajout d'une source de données à un modèle existant, vous utilisez l'Assistant Importation de table pour vous connecter à une source de données et sélectionner des tables et des vues à importer dans le modèle. Dans l’Assistant Importation de table, dans la page **Sélectionner des tables et des vues** , vous pouvez utiliser la fonctionnalité **Aperçu Appliquer filtre** pour visualiser un échantillon (limité à 50 lignes) des données que vous allez importer. Vous pouvez également spécifier des filtres pour exclure des données qui ne doivent pas être incluses dans le modèle.  
  
 De la même façon, pour les modèles existants qui ont déjà été créés, vous pouvez utiliser la boîte de dialogue **Modifier les propriétés de la table** pour afficher un aperçu et filtrer les données importées dans une table. Les fonctionnalités de filtre et d'aperçu décrites ici utilisent les mêmes fonctionnalités que la fonctionnalité **Afficher un aperçu et appliquer le filtre** dans la page **Sélectionner des tables et des vues** de l'Assistant Importation de table.  
  
 La fonctionnalité **Aperçu Afficher filtre** et les boîtes de dialogue **Propriétés de la table** et **Gestionnaire de partitions** correspondent à une opération *côté client* in-process ; en fait, cette opération est différente de l’opération de connexion de la source de données et d’extraction depuis la source de données, qui est une opération côté serveur. Les informations d'identification utilisées pour afficher un aperçu et filtrer des données sont les informations d'identification de l'utilisateur actuellement connecté. Des opérations côté client utilisent toujours des informations d’identification Windows de l’utilisateur actuel pour se connecter à la source de données.  
  
 Cette séparation des informations d’identification utilisées pour une opération côté serveur et pour une opération côté client peut créer une incohérence entre ce que l’utilisateur voit via la fonctionnalité **Aperçu Afficher filtre** ou la boîte de dialogue **Propriétés de la table** (opération côté client) et les données qui sont extraites lors d’une importation ou d’un traitement (opération côté serveur). Si les informations d'identification de l'utilisateur actuellement connecté et les informations d'identification d'emprunt d'identité spécifiées sont différentes, les données qui s'affichent dans la fonctionnalité **Afficher un aperçu et appliquer le filtre** ou la boîte de dialogue **Propriétés de la table** et les données extraites pendant une importation ou un traitement peuvent être différentes selon les informations d'identification requises par la source de données.  
  
> [!IMPORTANT]  
>  Lorsque vous créez un modèle, assurez-vous que les informations d'identification de l'utilisateur actuellement connecté et les informations d'identification spécifiées pour l'emprunt d'identité disposent de droits suffisants pour extraire les données de la source de données.  
  
##  <a name="bkmk_imp_info_options"></a> Options  
 Lors de la configuration de l'emprunt d'identité, ou lorsque vous modifiez des propriétés pour une connexion à une source de données existante dans Analysis Services, vous pouvez spécifier l'une des options suivantes :  
  
|Option|ImpersonationMode<sup>1</sup>|Description|  
|------------|-----------------------------------|-----------------|  
|**Le nom d’utilisateur Windows spécifique et le mot de passe** <sup>2</sup>|ImpersonateWindowsUserAccount|Cette option spécifie que le modèle utilise un compte d'utilisateur Windows pour importer ou traiter des données à partir de la source de données. Le domaine et le nom du compte d’utilisateur utilise le format suivant : **\<nom de domaine >\\< nom du compte utilisateur\>** . Lors de la création d'un modèle à l'aide de l'Assistant Importation de table, c'est l'option par défaut.|  
|**Compte de service**|ImpersonateServiceAccount|Cette option spécifie que le modèle utilise les informations d'identification de sécurité associées à l'instance du service Analysis Services qui gère le modèle.|  
  
 <sup>1</sup>ImpersonationMode spécifie la valeur de la [DataSourceImpersonationInfo élément &#40;ASSL&#41; ](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl) propriété sur la source de données.  
  
 <sup>2</sup>lors de l’utilisation de cette option, si la base de données de l’espace de travail est supprimé de la mémoire, soit en raison d’un redémarrage ou le **rétention de l’espace de travail** propriété est définie sur **décharger de la mémoire** ou  **Supprimer à partir de l’espace de travail**, et le projet de modèle est fermé, dans la session suivante, si vous essayez de traiter les données de table, vous devrez entrer les informations d’identification pour chaque source de données. De la même façon, si une base de données model déployée est supprimée de la mémoire, vous serez invité à entrer les informations d'identification pour chaque source de données.  
  
##  <a name="bkmk_impers_sec"></a> Sécurité  
 Les informations d'identification utilisées avec l'emprunt d'identité sont rendues persistantes en mémoire par le moteur d'analyse en mémoire xVelocity (VertiPaq™) associé au serveur Analysis Services qui gère la base de données de l'espace de travail ou un modèle déployé.  À aucun moment les informations d'identification ne sont écrites sur le disque. Si la base de données d'espace de travail n'est pas en mémoire lorsque le modèle est déployé, l'utilisateur sera invité à entrer les informations d'identification utilisées pour se connecter à la source de données et pour extraire des données.  
  
> [!NOTE]  
>  Il est recommandé de spécifier un compte d'utilisateur Windows et un mot de passe pour les informations d'identification d'emprunt d'identité. Un compte d'utilisateur Windows peut être configuré avec des privilèges minimums pour se connecter aux données et les lire depuis la source de données.  
  
##  <a name="bkmk_imp_newmodel"></a> Emprunt d'identité lors de l'importation d'un modèle  
 Contrairement aux modèles tabulaires, qui peuvent utiliser plusieurs modes d'emprunt d'identité différents pour prendre en charge la collecte de données hors traitement, PowerPivot utilise un seul mode : ImpersonateCurrentUser. Étant donné que PowerPivot exécute toujours des opérations in-process, il se connecte aux sources de données à l'aide des informations d'identification de l'utilisateur actuellement connecté. Avec les modèles tabulaires, les informations d'identification de l'utilisateur actuellement connecté sont utilisées uniquement avec la fonctionnalité **Afficher un aperçu et appliquer le filtre** dans l'Assistant Importation de table et lors de la consultation des **Propriétés de la table**. Les informations d'identification d'emprunt d'identité sont utilisées lors de l'importation ou du traitement de données dans la base de données de l'espace de travail ou lors de l'importation ou du traitement des données dans un modèle déployé.  
  
 Lors de la création d'un modèle par importation d'un classeur PowerPivot existant, par défaut, le générateur de modèles configurera l'emprunt d'identité pour utiliser le compte de service (ImpersonateServiceAccount). Nous vous recommandons de modifier les informations d'identification d'emprunt d'identité sur les modèles importés de PowerPivot vers un compte d'utilisateur Windows. Une fois que le classeur PowerPivot a été importé et le nouveau modèle créé dans le Générateur de modèles, vous pouvez modifier les informations d’identification à l’aide de la **connexions existantes** boîte de dialogue.  
  
 Lors de la création d'un modèle importé à partir d'un modèle existant sur un serveur Analysis Services, les informations d'identification d'emprunt d'identité sont passées de la base de données model existante à la nouvelle base de données d'espace de travail modèle. Si nécessaire, vous pouvez modifier les informations d'identification sur le nouveau modèle à l'aide de la boîte de dialogue **Connexions existantes** .  
  
##  <a name="bkmk_conf_imp_info"></a> Configuration de l'emprunt d'identité  
 L'emplacement et le contexte d'un modèle détermineront la façon dont les informations d'emprunt d'identité sont configurées. Pour les modèles en cours de création dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], vous pouvez configurer les informations d'emprunt d'identité sur la page **Informations d'emprunt d'identité** dans l'Assistant Importation de table ou en modifiant une connexion à la source de données dans la boîte de dialogue **Connexions existantes** . Pour consulter les connexions existantes, dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], dans le menu **Modèle** , cliquez sur **Connexions existantes**.  
  
 Pour les modèles qui sont déployés sur un serveur Analysis Services, les informations de l’emprunt d’identité peuvent être configurées en cliquant sur les points de suspension (...) de la **informations d’emprunt d’identité de Source de données** propriété dans le **propriétés de la base de données** boîte de dialogue de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Mode DirectQuery &#40;SSAS Tabulaire&#41;](directquery-mode-ssas-tabular.md)   
 [Sources de données &#40;SSAS Tabulaire&#41;](../data-sources-ssas-tabular.md)   
 [Déploiement d’une solution de modèle tabulaire &#40;SSAS Tabulaire&#41;](tabular-model-solution-deployment-ssas-tabular.md)  
  
  
