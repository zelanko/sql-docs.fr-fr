---
title: "Débogage du Code d’Extension de remise | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
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
- delivery extensions [Reporting Services], debugging
- debugging delivery extensions [Reporting Services]
- troubleshooting [Reporting Services], delivery extensions
ms.assetid: a7d959da-5005-4a50-aca7-2cef36aa9947
caps.latest.revision: 35
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: e2d2162167123c152cbbeb58739f25ee06ec692a
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="debugging-delivery-extension-code"></a>Débogage du code d'extension de remise
  Le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] fournit plusieurs outils de débogage qui peuvent vous aider à analyser votre code d’extension de remise et localiser les erreurs qu’il contient. L'outil le plus approprié dépend de ce que vous essayez d'accomplir. Cet exemple utilise [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)].  
  
#### <a name="to-debug-your-delivery-extension-code"></a>Pour déboguer votre code d'extension de remise  
  
1.  Lancez [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)] et ouvrez votre projet d’extension de remise.  
  
2.  Générez le projet et déployez votre assembly d'extension de remise ainsi que le fichier .pdb associé sur le serveur de rapports et le Générateur de rapports. Pour plus d’informations sur le déploiement, consultez [déploiement d’une Extension de remise](../../../reporting-services/extensions/delivery-extension/deploying-a-delivery-extension.md).  
  
3.  Si vous avez écrit une interface utilisateur d'abonnement pour étendre le Gestionnaire de rapports, ouvrez Internet Explorer et naviguez jusqu'au Gestionnaire de rapports en laissant votre code d'extension de remise ouvert dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. Si vous n'avez pas d'interface utilisateur d'abonnement déployée pour le Gestionnaire de rapports, ouvrez simplement l'application cliente dans laquelle vous appelez votre extension de remise à l'aide de l'API SOAP.  
  
4.  Naviguez jusqu'à [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] et votre projet d'extension de remise et définissez des points d'arrêt dans votre code.  
  
5.  Le projet d’extension de remise demeurant dans la fenêtre active, cliquez sur **attacher au processus** sur la **déboguer** menu.  
  
     Le **attacher au processus** boîte de dialogue s’ouvre.  
  
6.  Dans la liste de processus, sélectionnez le processus aspnet_wp.exe (ou w3wp.exe si votre application est déployée sur IIS 6.0), puis cliquez sur **attacher**.  
  
7.  Définissez un nouvel abonnement à l'aide de votre extension de remise. Vous utiliserez très probablement le Gestionnaire de rapports ou l'API SOAP. Celle-ci doit appeler le débogueur et exécuter le code correspondant à vos points d'arrêt.  
  
8.  Parcourir votre code en utilisant le **F11** clé. Pour plus d'informations sur l'utilisation de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] pour le débogage, consultez votre documentation [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’une Extension de remise](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Bibliothèque d’Extension de Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
