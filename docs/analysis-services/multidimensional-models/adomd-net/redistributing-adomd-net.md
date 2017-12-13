---
title: "Redistribution d’ADOMD.NET | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- ADOMD.NET, redistributing
- redistributing ADOMD.NET
ms.assetid: f8db3c99-0243-4b92-b486-0d8786c264f4
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8c87db9dd22e53f8335dcbbb4994cd0835dfafcb
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="redistributing-adomdnet"></a>Redistribution d'ADOMD.NET
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Lorsque vous écrivez une application qui utilise ADOMD.NET, vous devez redistribuer la version appropriée d’ADOMD.NET en même temps que votre application. Pour redistribuer ADOMD.NET, incluez le programme d'installation ADOMD.NET dans le programme d'installation de votre application.  
  
 Le programme d'installation d'ADOMD.NET, ainsi que la dernière version d'ADOMD.NET, sont disponibles dans le Centre de téléchargement Microsoft dans le cadre de SQL Server Feature Pack.  
  
 Le programme d’installation ADOMD.NET installe les fichiers ADOMD.NET dans \< *lecteur système*> : \Program Files\Microsoft.NET\ADOMD.NET\\*numéro de version*.  
  
 Après avoir inclus le programme d'installation ADOMD.NET, faites en sorte que le programme d'installation de votre application lance le programme d'installation ADOMD.NET et installez ADOMD.NET. En outre, selon votre environnement, vous devrez peut-être veiller à ce que les assemblys associés soient approuvés par SQL Server.  
  
 Pour plus d'informations, consultez :  
  
 [Feature Pack pour Microsoft SQL Server](http://go.microsoft.com/fwlink/?LinkId=389949)  
  
 [Microsoft Connect : Dépendances ADOMD.NET](http://go.microsoft.com/fwlink/?LinkId=389950)  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation du Client ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)   
 [Programmation du serveur ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-server/adomd-net-server-programming.md)  
  
  
