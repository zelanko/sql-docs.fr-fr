---
title: "Signer un package &#224; l&#39;aide d&#39;un certificat num&#233;rique | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "signatures numériques [Integration Services]"
  - "signature de packages [Integration Services]"
  - "signatures [Integration Services]"
ms.assetid: 182b115e-0fe2-4717-8dff-183f9eb6e397
caps.latest.revision: 60
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 60
---
# Signer un package &#224; l&#39;aide d&#39;un certificat num&#233;rique
  Cette rubrique décrit comment signer un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] à l'aide d'un certificat numérique. Vous pouvez utiliser une signature numérique avec d'autres paramètres pour empêcher le chargement et l'exécution d'un package non valide.  
  
 Avant de pouvoir signer un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , vous devez effectuer les tâches suivantes :  
  
-   Créez ou obtenez une clé privée à associer au certificat et stockez cette clé privée sur l'ordinateur local.  
  
-   Obtenez un certificat en vue de la signature du code à partir d'une autorité de certification approuvée. Vous pouvez utiliser l'une des méthodes suivantes pour obtenir ou créer un certificat :  
  
    -   Obtenez un certificat à partir d'une autorité de certification commerciale publique qui émet des certificats.  
  
    -   Obtenez un certificat à partir d'un serveur de certificats, qui permet à une organisation d'émettre des certificats de façon interne. Vous devez ajouter le certificat racine utilisé pour signer le certificat dans le magasin **Autorités de certification racines de confiance** . Pour ajouter le certificat racine, vous pouvez utiliser le composant logiciel enfichable MMC ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console) Certificats. Pour plus d'informations, consultez la rubrique «[Services de certificats](http://go.microsoft.com/fwlink/?LinkId=100755)» dans MSDN Library (éventuellement en anglais).  
  
    -   Créez votre propre certificat à des fins de test uniquement. L'outil de création de certificat Makecert.exe génère des certificats X.509 à des fins de tests. Pour plus d’informations, consultez la rubrique « [Outil Certificate Creation Tool (Makecert.exe)](http://go.microsoft.com/fwlink/?LinkId=100756) » dans MSDN Library.  
  
     Pour plus d'informations sur les certificats, recherchez le composant logiciel enfichable Certificats dans l'aide en ligne. Pour plus d'informations sur la façon de signer des ressources numériques, consultez la rubrique «[Signature et vérification de code à l'aide d'Authenticode](http://go.microsoft.com/fwlink/?LinkId=78100)» dans MSDN Library (éventuellement en anglais).  
  
-   Assurez-vous que le certificat a été activé pour la signature de code. Pour déterminer si un certificat est activé pour la signature du code, examinez les propriétés du certificat dans le composant logiciel enfichable Certificats.  
  
-   Stockez le certificat dans le magasin Personnel.  
  
 Après avoir terminé les tâches précédentes, vous pouvez utiliser la procédure suivante pour signer un package.  
  
### Pour signer un package  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package à signer.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , dans le menu **SSIS** , cliquez sur **Signature numérique**.  
  
4.  Dans la boîte de dialogue **Signature numérique** , cliquez sur **Signer**.  
  
5.  Dans la boîte de dialogue **Sélectionner un certificat** , sélectionnez un certificat.  
  
6.  (Facultatif) Cliquez sur **Afficher le certificat** pour afficher les informations sur le certificat.  
  
7.  Cliquez sur **OK** pour fermer la boîte de dialogue **Sélectionner un certificat** .  
  
8.  Cliquez sur **OK** pour fermer la boîte de dialogue **Signature numérique** .  
  
9. Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
     Bien que le package ait été signé, vous devez maintenant configurer [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour vérifier la signature numérique avant de charger le package. Pour plus d’informations, consultez [Identifier la source de packages à l’aide de signatures numériques](../../integration-services/packages/identify-the-source-of-packages-with-digital-signatures.md).  
  
## Voir aussi  
 [Vue d’ensemble de la sécurité &#40;Integration Services&#41;](../../integration-services/security/security-overview-integration-services.md)  
  
  