---
title: Signer un Package à l’aide d’un certificat numérique | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- digital signatures [Integration Services]
- signing packages [Integration Services]
- signatures [Integration Services]
ms.assetid: 182b115e-0fe2-4717-8dff-183f9eb6e397
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c6da9652c18bd6e8093a38d337b61171bc448341
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62766601"
---
# <a name="sign-a-package-by-using-a-digital-certificate"></a>Signer un package à l'aide d'un certificat numérique
  Cette rubrique décrit comment signer un package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] à l'aide d'un certificat numérique. Vous pouvez utiliser une signature numérique avec d'autres paramètres pour empêcher le chargement et l'exécution d'un package non valide.  
  
 Avant de pouvoir signer un package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , vous devez effectuer les tâches suivantes :  
  
-   Créez ou obtenez une clé privée à associer au certificat et stockez cette clé privée sur l'ordinateur local.  
  
-   Obtenez un certificat en vue de la signature du code à partir d'une autorité de certification approuvée. Vous pouvez utiliser l'une des méthodes suivantes pour obtenir ou créer un certificat :  
  
    -   Obtenez un certificat à partir d'une autorité de certification commerciale publique qui émet des certificats.  
  
    -   Obtenez un certificat à partir d'un serveur de certificats, qui permet à une organisation d'émettre des certificats de façon interne. Vous devez ajouter le certificat racine utilisé pour signer le certificat dans le magasin **Autorités de certification racines de confiance** . Pour ajouter le certificat racine, vous pouvez utiliser le composant logiciel enfichable MMC ( [!INCLUDE[msCoName](../includes/msconame-md.md)] Management Console) Certificats. Pour plus d'informations, consultez la rubrique «[Services de certificats](https://go.microsoft.com/fwlink/?LinkId=100755)» dans MSDN Library (éventuellement en anglais).  
  
    -   Créez votre propre certificat à des fins de test uniquement. L'outil de création de certificat Makecert.exe génère des certificats X.509 à des fins de tests. Pour plus d’informations, consultez la rubrique «[Outil Certificate Creation Tool (Makecert.exe)](https://go.microsoft.com/fwlink/?LinkId=100756)» dans MSDN Library.  
  
     Pour plus d'informations sur les certificats, recherchez le composant logiciel enfichable Certificats dans l'aide en ligne. Pour plus d'informations sur la façon de signer des ressources numériques, consultez la rubrique «[Signature et vérification de code à l'aide d'Authenticode](https://go.microsoft.com/fwlink/?LinkId=78100)» dans MSDN Library (éventuellement en anglais).  
  
-   Assurez-vous que le certificat a été activé pour la signature de code. Pour déterminer si un certificat est activé pour la signature du code, examinez les propriétés du certificat dans le composant logiciel enfichable Certificats.  
  
-   Stockez le certificat dans le magasin Personnel.  
  
 Après avoir terminé les tâches précédentes, vous pouvez utiliser la procédure suivante pour signer un package.  
  
### <a name="to-sign-a-package"></a>Pour signer un package  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package à signer.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] , dans le menu **SSIS** , cliquez sur **Signature numérique**.  
  
4.  Dans la boîte de dialogue **Signature numérique** , cliquez sur **Signer**.  
  
5.  Dans la boîte de dialogue **Sélectionner un certificat** , sélectionnez un certificat.  
  
6.  (Facultatif) Cliquez sur **Afficher le certificat**pour afficher les informations sur le certificat.  
  
7.  Cliquez sur **OK** pour fermer la boîte de dialogue **Sélectionner un certificat** .  
  
8.  Cliquez sur **OK** pour fermer la boîte de dialogue **Signature numérique** .  
  
9. Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
     Bien que le package ait été signé, vous devez maintenant configurer [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] pour vérifier la signature numérique avant de charger le package. Pour plus d’informations, consultez [Identifier la source de packages à l’aide de signatures numériques](security/identify-the-source-of-packages-with-digital-signatures.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la sécurité &#40;Integration Services&#41;](security/security-overview-integration-services.md)  
  
  
