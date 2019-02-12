---
title: Suppression d’une extension de remise | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- removing delivery extensions
- deleting delivery extensions
- delivery extensions [Reporting Services], removing
ms.assetid: dcb7caf2-d19a-4bc5-afb3-2b61ad11cac5
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 5efe51d0c91a0321a17e539aeddbb26f0dc3a5fe
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56036249"
---
# <a name="removing-a-delivery-extension"></a>Suppression d'une extension de remise
  Pour supprimer une extension de remise [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], supprimez simplement l’élément **Extension** de votre extension de remise du fichier de configuration. Une fois les informations de configuration supprimées, l'extension de remise n'est plus disponible pour le serveur de rapports.  
  
 Une fois que l’élément **Extension** correspondant d’une extension de remise est supprimé du fichier de configuration, il n’est plus inscrit auprès du serveur de rapports. Le serveur de rapports supprime l'entrée dans la liste d'extensions de remise et désactive tous les abonnements qui utilisent cette extension de remise. Lorsqu'une extension de remise est supprimée, les utilisateurs ne sont plus en mesure de le sélectionner comme méthode de notification.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’une extension de remise](implementing-a-delivery-extension.md)   
 [Bibliothèque d'extensions Reporting Services](../reporting-services-extension-library.md)  
  
  
