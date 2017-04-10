---
title: "Propri&#233;t&#233;s r&#233;seau | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "LingerTimeout, propriété"
  - "EnableNagleAlgorithm, propriété"
  - "MinPendingAcceptExCount, propriété"
  - "MaxPendingSendCount, propriété"
  - "EnableBinaryXML, propriété"
  - "MinPendingReceiveCount, propriété"
  - "MaxCompletedReceiveCount, propriété"
  - "DisableNonblockingMode, propriété"
  - "RequestSizeThreshold, propriété"
  - "CompressionLevel, propriété"
  - "ReceiveBufferSize, propriété"
  - "EnableCompression, propriété"
  - "ServerSendTimeout, propriété"
  - "IPV4Support, propriété"
  - "MaxPendingReceiveCount, propriété"
  - "MaxPendingAcceptExCount, propriété"
  - "IPV6Support, propriété"
  - "MaxAllowedRequestSize, propriété"
  - "ServerReceiveTimeout, propriété"
  - "EnableLingerOnClose, propriété"
  - "InitialConnectTimeout, propriété"
  - "SendBufferSize, propriété"
  - "ScatterReceiveMultiplier, propriété"
  - "propriétés du réseau [Analysis Services]"
ms.assetid: ef4251e2-abe5-4c5b-9868-7549782d0244
caps.latest.revision: 15
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 15
---
# Propri&#233;t&#233;s r&#233;seau
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend en charge les propriétés de serveur répertoriées dans les tableaux suivants. Pour plus d’informations sur les autres propriétés de serveur et sur la façon de les configurer, consultez [Propriétés du serveur dans Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).  
  
 **S'applique à :** mode serveur multidimensionnel et tabulaire  
  
## Général  
 **ListenOnlyOnLocalConnections**  
 Propriété booléenne qui spécifie si l'écoute doit avoir lieu uniquement sur les connexions locales, par exemple localhost.  
  
## Port d'écoute  
 **IPV4Support**  
 Propriété dont la valeur est un entier 32 bits signé qui définit la prise en charge du protocole IPv4. Cette propriété peut prendre l'une des valeurs répertoriées dans le tableau suivant :  
  
|Valeur|Description|  
|-----------|-----------------|  
|*0*|IPv4 est désactivé ; les clients ne peuvent pas se connecter.|  
|*1*|(Valeur par défaut) IPv4 est requis ; le serveur ne démarrera pas s'il ne peut pas écouter IPv4.|  
|*2*|IPv4 est facultatif ; le serveur essaie d'écouter IPv4 mais démarre même s'il n'y parvient pas.|  
  
 **IPV6Support**  
 Propriété dont la valeur est un entier 32 bits signé qui définit la prise en charge du protocole IPv6. Cette propriété peut prendre l'une des valeurs répertoriées dans le tableau suivant :  
  
|Valeur|Description|  
|-----------|-----------------|  
|*0*|IPv6 est désactivé ; les clients ne peuvent pas se connecter.|  
|*1*|(Valeur par défaut) IPv6 est requis ; le serveur ne démarrera pas s'il ne peut pas écouter IPv6.|  
|*2*|IPv6 est facultatif ; le serveur essaie d'écouter IPv6 mais démarre même s'il n'y parvient pas.|  
  
 **MaxAllowedRequestSize**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **RequestSizeThreshold**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **ServerReceiveTimeout**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **ServerSendTimeout**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## Demandes  
 **EnableBinaryXML**  
 Propriété booléenne qui spécifie si le serveur prend en charge les demandes au format XML binaire.  
  
 **EnableCompression**  
 Propriété booléenne qui spécifie si la compression est activée pour les demandes.  
  
## Réponses  
 **CompressionLevel**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **EnableBinaryXML**  
 Propriété booléenne qui spécifie si le serveur prend en charge les réponses au format XML binaire.  
  
 **EnableCompression**  
 Propriété booléenne qui spécifie si la compression est activée pour les réponses aux demandes des clients.  
  
## TCP  
 **InitialConnectTimeout**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MaxCompletedReceiveCount**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MaxPendingAcceptExCount**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MaxPendingReceiveCount**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MaxPendingSendCount**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MinPendingAcceptExCount**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MinPendingReceiveCount**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **ScatterReceiveMultiplier**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **SocketOptions\ DisableNonblockingMode**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **SocketOptions\ EnableLingerOnClose**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **SocketOptions\EnableNagleAlgorithm**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **SocketOptions\ LingerTimeout**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **SocketOptions\ ReceiveBufferSize**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **SocketOptions\ SendBufferSize**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## Voir aussi  
 [propriétés du serveur dans Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Déterminer le mode serveur d'une instance Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  