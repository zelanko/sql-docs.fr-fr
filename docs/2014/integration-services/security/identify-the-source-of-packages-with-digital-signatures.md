---
title: Identifier la source de packages à l’aide de signatures numériques | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- signing packages [Integration Services]
- certificates [Integration Services]
- packages [Integration Services], security
- security [Integration Services], certificates
- signing policies [Integration Services]
ms.assetid: a433fbef-1853-4740-9d5e-8a32bc4ffbb2
caps.latest.revision: 45
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3b744fb7d966fc7079cf05072f94f425d79e2b34
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37320659"
---
# <a name="identify-the-source-of-packages-with-digital-signatures"></a>Identifier la source de packages à l'aide de signatures numériques
  Il est possible de signer un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] avec un certificat numérique pour identifier sa source. Après avoir signé un package avec un certificat numérique, vous pouvez utiliser [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour vérifier la signature numérique avant de charger le package. Pour vérifier la signature à l’aide d’ [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , vous devez définir une option dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ou dans l’utilitaire **dtexec** (dtexec.exe), ou définir une valeur de Registre facultative.  
  
## <a name="signing-a-package-with-a-digital-certificate"></a>Signature d'un package à l'aide d'un certificat numérique  
 Avant de pouvoir signer un package avec un certificat numérique, vous devez obtenir ou créer le certificat. Une fois que vous possédez le certificat, vous pouvez l'utiliser pour signer le package. Pour plus d’informations sur la façon d’obtenir un certificat et de signer un package avec ce certificat, consultez [Signer un package à l’aide d’un certificat numérique](../sign-a-package-by-using-a-digital-certificate.md).  
  
## <a name="setting-an-option-to-check-the-package-signature"></a>Définition d'une option pour vérifier la signature d'un package  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] et l’utilitaire **dtexec** proposent tous les deux une option qui configure [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour la vérification de la signature numérique d’un package signé. L’utilisation de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ou de l’utilitaire **dtexec** dépend de si vous souhaitez vérifier tous les packages ou simplement des packages spécifiques :  
  
-   Pour vérifier la signature numérique de tous les packages avant de charger les packages au moment de la conception, définissez l'option **Vérifier la signature numérique lors du chargement d'un package** dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Cette option est un paramètre global pour tous les packages dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Pour plus d'informations, consultez [General Page](../general-page-of-integration-services-designers-options.md).  
  
-   Pour vérifier la signature numérique d’un package individuel, spécifiez la `/VerifyS[igned]` option lorsque vous utilisez le **dtexec** utilitaire pour exécuter le package. Pour plus d’informations, voir [dtexec Utility](../packages/dtexec-utility.md).  
  
## <a name="setting-a-registry-value-to-check-the-package-signature"></a>Définition d'une valeur du Registre pour vérifier la signature d'un package  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] prend également en charge une valeur de Registre facultative, **BlockedSignatureStates**, que vous pouvez utiliser pour gérer la stratégie de chargement des packages signés et non signés d’une organisation. La valeur de Registre peut empêcher le chargement de packages si les packages ne sont pas signés ou s'ils possèdent des signatures non valides ou non approuvées. Pour plus d’informations sur la définition de cette valeur de Registre, consultez [Implémenter une stratégie de signature en définissant une valeur du Registre](../implement-a-signing-policy-by-setting-a-registry-value.md).  
  
> [!NOTE]  
>  La valeur de Registre **BlockedSignatureStates** facultative peut spécifier un paramètre plus restrictif que l’option de signature numérique définie dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ou au niveau de la ligne de commande **dtexec** . Dans cette situation, le paramètre du Registre plus restrictif a priorité sur les autres paramètres.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services &#40;SSIS&#41; Packages](../integration-services-ssis-packages.md)   
 [Vue d’ensemble de la sécurité &#40;Integration Services&#41;](security-overview-integration-services.md)  
  
  
