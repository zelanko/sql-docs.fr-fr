---
title: "Débogage du Code d’Extension de traitement des données | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- debugging data processing extensions [Reporting Services]
- troubleshooting [Reporting Services], data processing extensions
- data processing extensions [Reporting Services], debugging
ms.assetid: e963e205-9ae0-446d-97df-028a1d2727d9
caps.latest.revision: 40
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 0b7ee42be2f3d54fc8fb19ab48b3b603e29669e2
ms.contentlocale: fr-fr
ms.lasthandoff: 08/12/2017

---
# <a name="debugging-data-processing-extension-code"></a>Débogage du code des extensions pour le traitement des données
  Le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] fournit plusieurs outils de débogage qui peuvent vous aider à analyser votre code d’extension de traitement des données et recherchez les erreurs qu’il contient. L'outil le plus approprié dépend de ce que vous essayez d'accomplir. Cet exemple utilise [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)].  
  
#### <a name="to-debug-your-data-processing-extension-code"></a>Pour déboguer le code de votre extension pour le traitement des données  
  
1.  Lancez [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)] et ouvrez votre projet d'extension pour le traitement des données.  
  
2.  Générez le projet et déployez votre assembly d'extension pour le traitement des données ainsi que le fichier .pdb associé sur le Générateur de rapports. Pour plus d’informations sur le déploiement, consultez [Comment : déployer une Extension de traitement de données au Concepteur de rapports](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension-to-report-designer.md).  
  
3.  Ouvrez un nouveau projet de rapport dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] tout en laissant ouvert le code de votre extension pour le traitement des données dans une fenêtre distincte de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
4.  Accédez à la fenêtre de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] qui contient votre projet d'extension pour le traitement des données et définissez des points d'arrêt dans votre code.  
  
5.  Le traitement des données fenêtre extension pour le projet toujours active, puis cliquez sur **attacher au processus** sur la **déboguer** menu.  
  
     Le **attacher au processus** boîte de dialogue s’ouvre.  
  
6.  Dans la liste de processus, sélectionnez le processus devenv.exe qui correspond à votre projet de rapport et cliquez sur **attacher**.  
  
7.  Définissez votre source de données de rapport à l’aide du **les données de rapport** onglet du projet de rapport. Vous utiliserez très probablement le Concepteur de requêtes générique pour exécuter une requête sur votre source de données personnalisée. Celle-ci doit appeler le débogueur et exécuter le code correspondant à vos points d'arrêt.  
  
8.  Exécutez le code pas à pas à l'aide de la touche F11. Pour plus d'informations sur l'utilisation de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] pour le débogage, consultez votre documentation [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’une Extension de traitement des données](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)   
 [Extensions Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Implémentation d’une Extension de traitement des données](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Bibliothèque d’Extension de Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  

