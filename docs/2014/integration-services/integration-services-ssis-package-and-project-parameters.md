---
title: Paramètres Integration Services (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9ed9ca8e-8b1e-48d9-907d-285516d6562b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 980f25c181556ee50a51bc57dce39b60cae322fc
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85436386"
---
# <a name="integration-services-ssis-parameters"></a>Paramètres Integration Services (SSIS)
  Les paramètres[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS) vous permettent d'affecter des valeurs aux propriétés dans des packages au moment de l'exécution du package. Vous pouvez créer des *paramètres de projet* au niveau du projet et des *paramètres de package* au niveau du package. Les paramètres du projet sont utilisés pour fournir une entrée externe que le projet reçoit à un ou plusieurs packages du projet. L'utilisation de paramètres de package vous permet de modifier l'exécution du package sans avoir à modifier et à redéployer le package.  
  
 Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] vous créez, modifiez ou supprimez les paramètres d'un projet à l'aide de la fenêtre **Project.params** . Vous créez, modifiez et supprimez les paramètres d'un package à l'aide de l'onglet **Paramètres** dans le Concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] . Vous associez un nouveau paramètre ou un paramètre existant à une propriété de tâche à l'aide de la boîte de dialogue **Paramétrer** . Pour plus d'informations sur l'utilisation de la fenêtre **Project.params** et l'onglet **Paramètres** , consultez [Create Parameters](create-parameters.md). Pour plus d'informations sur la boîte de dialogue **Paramétrer** , consultez [Parameterize Dialog Box](parameterize-dialog-box.md).  
  
## <a name="parameters-and-package-deployment-model"></a>Paramètres et modèle de déploiement de package  
 En général, si vous déployez un package à l'aide du modèle de déploiement de package, vous devez utiliser les configurations au lieu des paramètres.  
  
 Lorsque vous déployez un package qui contient des paramètres à l'aide du modèle de déploiement de package, puis exécutez le package, les paramètres ne sont pas appelés au moment de l'exécution. Si le package contient des paramètres de package et des expressions dans le package utilisent les paramètres, les valeurs résultantes sont appliquées au moment de l'exécution. Si le package contient des paramètres de projet, l'exécution du package peut échouer.  
  
## <a name="parameters-and-project-deployment-model"></a>Paramètres et modèle de déploiement de projet  
 Lorsque vous déployez un projet sur le serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , vous utilisez des vues, des procédures stockées et l'interface utilisateur [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour exécuter le projet et les paramètres du package. Pour plus d'informations, consultez les rubriques ci-dessous.  
  
-   [Vues &#40;catalogue Integration Services&#41;](/sql/integration-services/system-views/views-integration-services-catalog)  
  
-   [Procédures stockées &#40;catalogue Integration Services&#41;](/sql/integration-services/system-stored-procedures/stored-procedures-integration-services-catalog)  
  
-   [Boîte de dialogue Configurer](catalog/configure-dialog-box.md)  
  
-   [Exécuter le package, boîte de dialogue](../../2014/integration-services/execute-package-dialog-box.md)  
  
### <a name="parameter-values"></a>Valeurs des paramètres  
 Attribuez au plus trois types différents de valeurs à un paramètre. Lorsque l'exécution d'un package démarre, une valeur unique est utilisée pour le paramètre, et le paramètre est résolu à sa valeur littérale finale.  
  
 Le tableau qui suit énumère les types de valeurs.  
  
|Nom de la valeur|Description|Type de la valeur|  
|----------------|-----------------|-------------------|  
|Valeur d'exécution|Valeur affectée à une instance spécifique de l'exécution du package. Cette affectation remplace toutes les autres valeurs, mais s'applique uniquement à une instance unique de l'exécution du package.|Littéral|  
|Valeur de serveur|Valeur affectée au paramètre dans l'étendue du projet après que le projet est déployé sur le serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Cette valeur remplace la valeur de conception par défaut.|Littéral ou Référence de variable d'environnement|  
|Valeur de création|Valeur affectée au paramètre lorsque le projet est créé ou modifié dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]. Cette valeur est conservée avec le projet.|Littéral|  
  
 Utilisez un paramètre unique pour affecter une valeur à plusieurs propriétés des packages. Il n'est possible d'affecter une valeur à une propriété de package unique qu'à partir d'un paramètre unique.  
  
###  <a name="executions-and-parameter-values"></a><a name="executions"></a> Exécutions et valeurs de paramètres  
 L' *exécution* est un objet qui représente une instance unique de l'exécution du package. Lorsque vous créez une exécution, vous spécifiez tous les détails nécessaires pour exécuter un package, tel que les valeurs de paramètres d'exécution. Vous pouvez également modifier les valeurs de paramètres pour les exécutions existantes.  
  
 Lorsque vous définissez de manière explicite une valeur de paramètre d'exécution, cette valeur s'applique uniquement à cette instance d'exécution particulière. La valeur d'exécution est utilisée à la place d'une valeur de serveur ou d'une valeur de conception. Si vous ne définissez pas de valeur d'exécution de manière explicite, et qu'une valeur de serveur a été spécifiée, la valeur de serveur est utilisée.  
  
 Lorsqu'un paramètre est marqué comme requis, une valeur de serveur ou une valeur d'exécution doit être spécifiée pour ce paramètre. Sinon, le package correspondant ne s'exécute pas. Bien que le paramètre dispose d'une valeur par défaut au moment de la conception, elle ne sera jamais utilisée une fois le projet déployé.  
  
#### <a name="environment-variables"></a>Variables d'environnement  
 Si un paramètre référence une variable d'environnement, la valeur littérale de cette variable est résolue par l'intermédiaire de la référence environnementale spécifiée et est appliquée au paramètre. La valeur de paramètre littérale finale utilisée pour l'exécution du package est appelée « valeur de paramètre d'exécution ». Vous spécifiez la référence environnementale pour une exécution à l'aide de la boîte de dialogue **Exécuter** .  
  
 Si un paramètre de projet référence une variable d'environnement et la valeur littérale de la variable n'est pas résolue au moment de l'exécution, la valeur de conception est utilisée. La valeur de serveur n'est pas utilisée.  
  
 Pour afficher les variables d'environnement affectées aux valeurs de paramètre, interrogez l'affichage catalog.object_parameters. Pour plus d’informations, consultez [catalog.object_parameters &#40;base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database).  
  
#### <a name="determining-execution-parameter-values"></a>Détermination des valeurs de paramètre d'exécution  
 La procédure stockée et les vues Transact-SQL suivantes peuvent être utilisées pour afficher et définir des valeurs de paramètre.  
  
 [catalog.execution_parameter_values &#40;base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-execution-parameter-values-ssisdb-database) (vue)  
 Affiche les valeurs de paramètre effectives qui seront utilisées par une exécution spécifique  
  
 [catalog.get_parameter_values &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-get-parameter-values-ssisdb-database) (procédure stockée)  
 Résout et affiche les valeurs effectives du package et de la référence environnementale spécifiés  
  
 [catalog.object_parameters &#40;base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database) (vue)  
 Affiche les paramètres et les propriétés de tous les packages et les projets dans le catalogue [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , y compris les valeurs de conception par défaut et les valeurs de serveur par défaut.  
  
 [catalog.set_execution_parameter_value &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database)  
 Définit la valeur d'un paramètre pour une instance d'exécution dans le catalogue [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
 Vous pouvez également utiliser la boîte de dialogue **Exécuter le package** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour modifiez la valeur de paramètre. Pour plus d'informations, consultez [Execute Package Dialog Box](../../2014/integration-services/execute-package-dialog-box.md).  
  
 Vous pouvez également utiliser l'option `/Parameter` dtexec pour modifier une valeur de paramètre. Pour plus d'informations, consultez [Utilitaire dtexec](packages/dtexec-utility.md).  
  
### <a name="parameter-validation"></a>Validation des paramètres  
 Si les valeurs de paramètre ne peuvent pas être résolues, l'exécution du package correspondante échoue. Pour éviter les échecs, vous pouvez valider les projets et les packages à l'aide de la boîte de dialogue **Valider** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. La validation vous permet de vérifier que tous les paramètres disposent des valeurs nécessaires ou qu'ils peuvent résoudre les valeurs requises avec des références environnementales spécifiques. La validation vérifie également d'autres problèmes courants liés aux packages.  
  
 Pour plus d'informations, consultez [Validate Dialog Box](catalog/validate-dialog-box.md).  
  
### <a name="parameter-example"></a>Exemple de paramètres  
 Cet exemple illustre un paramètre nommé **pkgOptions** utilisé pour spécifier les options du package dans lequel il réside.  
  
 Au moment de la conception, lorsque le paramètre a été créé dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], la valeur par défaut 1 a été affectée au paramètre. Cette valeur par défaut est appelée « valeur de conception par défaut ». Si le projet a été déployé dans le catalogue SSISDB et qu'aucune autre valeur n'a été affectée à ce paramètre, la propriété de package correspondant au paramètre **pkgOptions** se verrait affecter la valeur 1 pendant l'exécution du package. La valeur de conception par défaut est conservée avec le projet pendant tout son cycle de vie.  
  
 Lors de la préparation une instance spécifique de l'exécution du package, la valeur 5 est affectée au paramètre **pkgOptions** . Cette valeur est appelée « valeur d'exécution » car elle s'applique au paramètre uniquement pour cette instance d'exécution particulière. Lorsque l'exécution démarre, la propriété de package correspondant au paramètre **pkgOptions** se voit affecter la valeur 5.  
  
## <a name="related-tasks"></a>Tâches associées  
 [Créer des paramètres](create-parameters.md)  
  
 [Définir des valeurs de paramètres après le déploiement du projet](../../2014/integration-services/set-parameter-values-after-the-project-is-deployed.md)  
  
## <a name="related-content"></a>Contenu associé  
 Entrée de blog, [Astuce rapide SSIS : Paramètres requis](https://go.microsoft.com/fwlink/?LinkId=239781), sur le site mattmasson.com.  
  
  
