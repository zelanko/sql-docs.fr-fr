---
title: L’emprunt d’identité dans les modèles tabulaires Analysis Services | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 724d9220f156cb9b2a00e3bd12a15f35750de652
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52416019"
---
# <a name="impersonation"></a>Emprunt d'identité 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Cet article explique aux créateurs de modèles tabulaires comment informations d’identification d’ouverture de session sont utilisées par Analysis Services lors de la connexion à une source de données pour importer et traiter (Actualiser) des données.  

##  <a name="bkmk_conf_imp_info"></a> Configuration de l’emprunt d’identité  
 Il existe un modèle où et dans quel contexte détermine comment les informations d’emprunt d’identité sont configurées. Lorsque vous créez un nouveau projet de modèle, l’emprunt d’identité est configuré dans SQL Server Data Tools (SSDT) lorsque vous vous connectez à une source de données pour importer des données. Une fois qu’un modèle est déployé, l’emprunt d’identité peut être configuré dans la propriété de chaîne de connexion de base de données modèle à l’aide de SQL Server Management Studio (SSMS). Pour les modèles tabulaires dans Azure Analysis Services, vous pouvez utiliser SSMS ou **afficher en tant que : Script** mode dans le concepteur basée sur navigateur pour modifier le fichier Model.bim au format JSON.
  
##  <a name="bkmk_how_imper"></a> Utilisation de l’emprunt d’identité  
 L'*emprunt d'identité* est la capacité d'une application serveur, telle qu'Analysis Services, d'assumer l'identité d'une application cliente. Analysis Services s’exécute à l’aide d’un compte de service, toutefois, lorsque le serveur établit une connexion à une source de données, il utilise l’emprunt d’identité afin que les vérifications d’accès pour l’importation de données et de traitement peut être effectuée.  
  
 Informations d’identification utilisées pour l’emprunt d’identité sont différentes de celles que vous êtes actuellement connecté avec. L’utilisateur connecté sont utilisées pour certaines opérations côté client lors de la création d’un modèle.  
  
 Il est important pour comprendre comment les informations d’identification d’emprunt d’identité sont spécifiées et sécurisées, ainsi que la différence entre les contextes dans les deux lequel vous êtes connecté sur les informations d’identification de l’utilisateur sont utilisées et lorsque les autres informations d’identification d’emprunt d’identité sont utilisées.  
  
 **Présentation des informations d’identification côté serveur**  
 
Lorsque les données sont importées ou traitées, les informations d’identification de l’emprunt d’identité sont utilisées pour vous connecter à la source de données et extraire les données. Il s’agit d’un *côté serveur* opération en cours d’exécution dans le contexte d’une application cliente, car le serveur Analysis Services qui héberge la base de données de l’espace de travail se connecte à la source de données et extrait les données.  
  
 Lorsque vous déployez un modèle sur un serveur Analysis Services, si la base de données d'espace de travail est en mémoire lorsque le modèle est déployé, les informations d'identification sont passées au serveur Analysis Services sur lequel le modèle est déployé. À aucun moment les informations d'identification de l'utilisateur sont stockées sur le disque.  
  
 Lorsqu’un modèle déployé traite des données à partir d’une source de données, les informations d’identification d’emprunt d’identité, rendues persistantes dans la base de données en mémoire, sont utilisées pour se connecter à la source de données et extraire les données. Étant donné que ce processus est géré par le serveur Analysis Services de gestion de la base de données model, voici à nouveau une opération côté serveur.  
  
 **Présentation des informations d’identification côté client**  
  
 Quand un nouveau modèle de création ou l’ajout d’une source de données à un modèle existant, vous vous connecter à une source de données et sélectionnez des tables et vues doivent être importées dans le modèle. Dans l’Assistant Importation de Table ou d’obtenir un concepteur Data\Query aperçu et filtrer les fonctionnalités, vous consultez un exemple de données que vous importez. Vous pouvez également spécifier des filtres pour exclure des données qui ne doivent pas être incluses dans le modèle.  
  
 De même, pour les modèles existants qui ont déjà été créés, vous utilisez le **propriétés de la Table** boîte de dialogue Aperçu et filtrer les données importées dans une table.  
  
 Les fonctionnalités de filtre et d’aperçu, **propriétés de la Table**, et **le Gestionnaire de Partition** boîtes de dialogue sont un processus *côté client* opération ; autrement dit, ce qui se fait au cours de cette opération diffèrent de mode de connexion à la source de données et les données sont extraites à partir de la source de données ; une opération côté serveur. Les informations d'identification utilisées pour afficher un aperçu et filtrer des données sont les informations d'identification de l'utilisateur actuellement connecté. En effet, vos informations d’identification. 
  
 La séparation des informations d’identification utilisées pendant côté serveur et les opérations côté client peuvent entraîner une incohérence entre ce que vous voyez et quelles données sont extraites pendant une importation ou d’un processus (opération côté serveur). Si les informations d’identification vous êtes actuellement connecté avec et les informations d’identification d’emprunt d’identité spécifiées sont différentes, les données que vous voyez dans les fonctionnalités de filtre et d’aperçu ou la **propriétés de la Table** boîte de dialogue et les données extraites pendant une importation ou processus peuvent être différent, selon les informations d’identification requises par la source de données.  
  
> [!IMPORTANT]  
>  Lorsque vous créez un modèle, assurez-vous que les informations d’identification que vous êtes connecté et les informations d’identification spécifiées pour l’emprunt d’identité disposent des droits suffisants pour extraire les données de la source de données.  
  
##  <a name="bkmk_imp_info_options"></a> Options  
 Lors de la configuration de l’emprunt d’identité, ou lorsque vous modifiez les propriétés pour une connexion de source de données existante, spécifiez l’une des options suivantes :  
  
**Modèles tabulaires 1400 et versions ultérieures**
 
|Option|Description|  
|------------|-----------------|  
|**Emprunter l’identité de compte**|Spécifie le modèle utilise un compte d’utilisateur Windows pour importer ou traiter les données de la source de données. Le domaine et le nom du compte d’utilisateur utilise le format suivant :**\<nom de domaine >\\< nom du compte utilisateur\>**.|  
|**Emprunter l’identité d’utilisateur actuel**|Spécifie les données doivent être accessibles à partir de la source de données à l’aide de l’identité de l’utilisateur qui a envoyé la demande. Ce mode s’applique uniquement au mode de requête directe.|  
|**Emprunter l’identité**|Spécifie un nom d’utilisateur pour accéder à la source de données, mais n’a pas besoin de spécifier le mot de passe du compte. Ce mode s’applique uniquement lorsque la délégation contrainte Kerberos est activée et spécifie que l’authentification S4U doit être utilisée.|  
|**Emprunter l’identité du compte de Service**|Spécifie le modèle utilise les informations d’identification de sécurité associées à l’instance de service Analysis Services qui gère le modèle.|  
|**Emprunter l’identité de compte sans assistance**|Spécifie que le moteur Analysis Services doit utiliser un compte sans assistance préconfiguré pour accéder aux données.|  


**Modèles 1200 tabulaires**
 
|Option|Description|  
|------------|-----------------|  
|**Mot de passe et le nom d’utilisateur Windows spécifique**|Cette option spécifie le modèle utilise un compte d’utilisateur Windows pour importer ou traiter les données de la source de données. Le domaine et le nom du compte d’utilisateur utilise le format suivant :**\<nom de domaine >\\< nom du compte utilisateur\>**. Lors de la création d'un modèle à l'aide de l'Assistant Importation de table, c'est l'option par défaut.|  
|**Compte de service**|Cette option spécifie que le modèle utilise les informations d'identification de sécurité associées à l'instance du service Analysis Services qui gère le modèle.|  
  
##  <a name="bkmk_impers_sec"></a> Sécurité  
 Informations d’identification utilisées avec l’emprunt d’identité sont rendues persistantes en mémoire par le moteur VertiPaq™. Informations d’identification ne sont jamais écrites sur le disque. Si la base de données de l’espace de travail n’est pas en mémoire lorsque le modèle est déployé, l’utilisateur est invité à entrer les informations d’identification utilisées pour se connecter aux source de données et extraire des données.  
  
> [!NOTE]  
>  Il est recommandé de spécifier un compte d'utilisateur Windows et un mot de passe pour les informations d'identification d'emprunt d'identité. Un compte d’utilisateur Windows peut être configuré pour utiliser les privilèges minimaux requis pour vous connecter à et lire des données à partir de la source de données.  
  

  
## <a name="see-also"></a>Voir aussi  
 [Mode DirectQuery](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [Sources de données](../../analysis-services/tabular-models/data-sources-ssas-tabular.md)   
 [Déploiement d’une solution de modèle tabulaire](../../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md)  
  
  
