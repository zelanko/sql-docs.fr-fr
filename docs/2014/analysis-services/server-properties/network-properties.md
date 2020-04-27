---
title: Propriétés du réseau | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- LingerTimeout property
- EnableNagleAlgorithm property
- MinPendingAcceptExCount property
- MaxPendingSendCount property
- EnableBinaryXML property
- MinPendingReceiveCount property
- MaxCompletedReceiveCount property
- DisableNonblockingMode property
- RequestSizeThreshold property
- CompressionLevel property
- ReceiveBufferSize property
- EnableCompression property
- ServerSendTimeout property
- IPV4Support property
- MaxPendingReceiveCount property
- MaxPendingAcceptExCount property
- IPV6Support property
- MaxAllowedRequestSize property
- ServerReceiveTimeout property
- EnableLingerOnClose property
- InitialConnectTimeout property
- SendBufferSize property
- ScatterReceiveMultiplier property
- network properties [Analysis Services]
ms.assetid: ef4251e2-abe5-4c5b-9868-7549782d0244
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 882b5fc60020423e19f68fda40273b7c944bd4f5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66068878"
---
# <a name="network-properties"></a>Propriétés réseau
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend en charge les propriétés de serveur répertoriées dans les tableaux suivants. Pour plus d'informations sur les autres propriétés de serveur et la façon de les configurer, consultez [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).  
  
 **S'applique à :** mode serveur multidimensionnel et tabulaire  
  
## <a name="general"></a>Général  
 `ListenOnlyOnLocalConnections`  
 Propriété booléenne qui spécifie si l'écoute doit avoir lieu uniquement sur les connexions locales, par exemple localhost.  
  
## <a name="listener"></a>Écouteur  
 `IPV4Support`  
 Propriété dont la valeur est un entier 32 bits signé qui définit la prise en charge du protocole IPv4. Cette propriété peut prendre l'une des valeurs répertoriées dans le tableau suivant :  
  
|Value|Description|  
|-----------|-----------------|  
|*0*|IPv4 est désactivé ; les clients ne peuvent pas se connecter.|  
|*1*|(Valeur par défaut) IPv4 est requis ; le serveur ne démarrera pas s'il ne peut pas écouter IPv4.|  
|*2*|IPv4 est facultatif ; le serveur essaie d'écouter IPv4 mais démarre même s'il n'y parvient pas.|  
  
 `IPV6Support`  
 Propriété dont la valeur est un entier 32 bits signé qui définit la prise en charge du protocole IPv6. Cette propriété peut prendre l'une des valeurs répertoriées dans le tableau suivant :  
  
|Value|Description|  
|-----------|-----------------|  
|*0*|IPv6 est désactivé ; les clients ne peuvent pas se connecter.|  
|*1*|(Valeur par défaut) IPv6 est requis ; le serveur ne démarrera pas s'il ne peut pas écouter IPv6.|  
|*2*|IPv6 est facultatif ; le serveur essaie d'écouter IPv6 mais démarre même s'il n'y parvient pas.|  
  
 `MaxAllowedRequestSize`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `RequestSizeThreshold`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ServerReceiveTimeout`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ServerSendTimeout`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="requests"></a>Demandes  
 `EnableBinaryXML`  
 Propriété booléenne qui spécifie si le serveur prend en charge les demandes au format XML binaire.  
  
 `EnableCompression`  
 Propriété booléenne qui spécifie si la compression est activée pour les demandes.  
  
## <a name="responses"></a>Réponses  
 `CompressionLevel`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `EnableBinaryXML`  
 Propriété booléenne qui spécifie si le serveur prend en charge les réponses au format XML binaire.  
  
 `EnableCompression`  
 Propriété booléenne qui spécifie si la compression est activée pour les réponses aux demandes des clients.  
  
## <a name="tcp"></a>TCP  
 `InitialConnectTimeout`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MaxCompletedReceiveCount`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MaxPendingAcceptExCount`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MaxPendingReceiveCount`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MaxPendingSendCount`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MinPendingAcceptExCount`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MinPendingReceiveCount`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ScatterReceiveMultiplier`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `SocketOptions\ DisableNonblockingMode`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `SocketOptions\ EnableLingerOnClose`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `SocketOptions\EnableNagleAlgorithm`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `SocketOptions\ LingerTimeout`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `SocketOptions\ ReceiveBufferSize`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `SocketOptions\ SendBufferSize`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les propriétés du serveur dans Analysis Services](server-properties-in-analysis-services.md)   
 [Déterminer le mode serveur d'une instance Analysis Services](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
