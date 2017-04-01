---
title: "Identifier la source de packages &#224; l&#39;aide de signatures num&#233;riques | Microsoft Docs"
ms.custom: ""
ms.date: "08/24/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "signature de packages [Integration Services]"
  - "certificats [Integration Services]"
  - "packages [Integration Services], sécurité"
  - "sécurité [Integration Services], certificats"
  - "stratégie de signature [Integration Services]"
ms.assetid: a433fbef-1853-4740-9d5e-8a32bc4ffbb2
caps.latest.revision: 46
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 46
---
# Identifier la source de packages &#224; l&#39;aide de signatures num&#233;riques
  Il est possible de signer un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] avec un certificat numérique pour identifier sa source. Après avoir signé un package avec un certificat numérique, vous pouvez utiliser [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour vérifier la signature numérique avant de charger le package. Pour vérifier la signature à l’aide d’[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous devez définir une option dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ou dans l’utilitaire **dtexec** (dtexec.exe), ou définir une valeur de Registre facultative.  
  
## Signer un package à l’aide d’un certificat numérique  
 Avant de pouvoir signer un package avec un certificat numérique, vous devez obtenir ou créer le certificat. Une fois que vous possédez le certificat, vous pouvez l'utiliser pour signer le package. Pour plus d’informations sur la façon d’obtenir un certificat et de signer un package avec ce certificat, consultez [Signer un package à l’aide d’un certificat numérique](../../integration-services/packages/sign-a-package-by-using-a-digital-certificate.md).  
  
## Définir une option pour vérifier la signature d’un package  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] et l’utilitaire **dtexec** proposent tous les deux une option qui configure [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour la vérification de la signature numérique d’un package signé. L’utilisation de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ou de l’utilitaire **dtexec** dépend de si vous souhaitez vérifier tous les packages ou simplement des packages spécifiques :  
  
-   Pour vérifier la signature numérique de tous les packages avant de charger les packages au moment de la conception, définissez l'option **Vérifier la signature numérique lors du chargement d'un package** dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Cette option est un paramètre global pour tous les packages dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].
  
-   Pour vérifier la signature numérique d’un package individuel, spécifiez l’option **/VerifyS[igned]** quand vous utilisez l’utilitaire **dtexec** pour exécuter le package. Pour plus d’informations, voir [dtexec Utility](../../integration-services/packages/dtexec-utility.md).  
  
## Définir une valeur du Registre pour vérifier la signature d’un package  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] prend également en charge une valeur de Registre facultative, **BlockedSignatureStates**, que vous pouvez utiliser pour gérer la stratégie de chargement des packages signés et non signés d’une organisation. La valeur de Registre peut empêcher le chargement de packages si les packages ne sont pas signés ou s'ils possèdent des signatures non valides ou non approuvées. Pour plus d’informations sur la définition de cette valeur de Registre, consultez [Implémenter une stratégie de signature en définissant une valeur du Registre](../../integration-services/packages/implement-a-signing-policy-by-setting-a-registry-value.md).  
  
> **REMARQUE :** la valeur de Registre **BlockedSignatureStates** facultative peut spécifier un paramètre qui est plus restrictif que l’option de signature numérique définie dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ou à la ligne de commande **dtexec**. Dans cette situation, le paramètre du Registre plus restrictif a priorité sur les autres paramètres.  
  
## Voir aussi  
 [Packages Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-packages.md)   
 [Vue d’ensemble de la sécurité &#40;Integration Services&#41;](../../integration-services/security/security-overview-integration-services.md)  
  
  