---
title: Implémenter une stratégie de signature en définissant une valeur de Registre | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- signing policies [Integration Services]
ms.assetid: 64f6966f-2292-401f-acb1-2ccb5aee484a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 1f0761f0485cea055e2317ca24b2931302431e5c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62893198"
---
# <a name="implement-a-signing-policy-by-setting-a-registry-value"></a>Implémenter une stratégie de signature en définissant une valeur du Registre
  Vous pouvez utiliser une valeur du Registre facultative pour gérer la stratégie d'une organisation pour charger des packages signés ou non signés. Si vous utilisez cette valeur du Registre, vous devez créer cette valeur du Registre sur tous les ordinateurs sur lesquels les packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] s'exécuteront et sur lesquels vous souhaitez appliquer la stratégie. Une fois la valeur du Registre définie, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] vérifiera les signatures avant de charger les packages.  
  
 La procédure décrite dans cette rubrique explique comment ajouter la valeur DWORD facultative `BlockedSignatureStates` à la clé de Registre HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS. La valeur de données dans `BlockedSignatureStates` détermine si un package doit être bloqué s'il possède une signature non approuvée, une signature non valide ou s'il n'est pas signé. En ce qui concerne l'état des signatures utilisées pour signer les packages, la valeur de Registre `BlockedSignatureStates` emploie les définitions suivantes :  
  
-   Une *signature valide* est une signature qui peut être lue correctement.  
  
-   Une *signature non valide* est une signature dont la somme de contrôle déchiffrée (hachage unidirectionnel du code de package chiffré par une clé privée) ne correspond pas à la somme de contrôle déchiffrée calculée dans le cadre du chargement des packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
-   Une *signature approuvée* est une signature créée à l’aide d’un certificat numérique signé par une autorité de certification racine de confiance. Ce paramètre n'exige pas la recherche du signataire dans la liste Éditeurs approuvés de l'utilisateur.  
  
-   Une *signature non approuvée* est une signature qui ne peut pas être vérifiée en tant que signature émise par une autorité de certification racine de confiance ou bien une signature qui n’est pas actuelle.  
  
 Le tableau suivant répertorie les valeurs valides des données DWORD et leur stratégie associée.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Pas de restriction administrative.|  
|1|Bloquer les signatures non valides.<br /><br /> Ce paramètre ne bloque pas les packages non signés.|  
|2|Bloquer les signatures non valides et non approuvées.<br /><br /> Ce paramètre ne bloque pas les packages non signés mais bloque les signatures générées automatiquement.|  
|3|Bloquer les signatures non valides et non approuvées et les packages non signés.<br /><br /> Ce paramètre bloque lui aussi les signatures générées automatiquement.|  
  
> [!NOTE]  
>  Le paramètre recommandé pour `BlockedSignatureStates` est 3. Ce paramètre offre une protection maximale contre des packages non signés ou des signatures non valides ou non approuvées. Néanmoins, ce paramètre recommandé peut ne pas convenir dans tous les cas. Pour plus d’informations sur la signature des ressources numériques, consultez la rubrique[Introduction to Code Signing](https://go.microsoft.com/fwlink/?LinkId=51414)(Introduction à la signature du code) dans MSDN Library.  
  
### <a name="to-implement-a-signing-policy-for-packages"></a>Pour implémenter une stratégie de signature pour des packages  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans la boîte de dialogue Exécuter, tapez `Regedit`, puis cliquez sur **OK**.  
  
3.  Localisez la clé de registre HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS.  
  
4.  Cliquez avec le bouton droit sur **MSDTS**, pointez sur **Nouveau**, puis cliquez sur **Valeur DWORD**.  
  
5.  Remplacez le nom de la nouvelle valeur par `BlockedSignatureStates`.  
  
6.  Avec le bouton droit `BlockedSignatureStates` et cliquez sur **modifier**.  
  
7.  Dans la boîte de dialogue **Édition de la valeur DWORD** , tapez la valeur 0, 1, 2 ou 3.  
  
8.  Cliquez sur **OK**.  
  
9. Dans le menu **Fichier** , cliquez sur **Quitter**.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la sécurité &#40;Integration Services&#41;](security/security-overview-integration-services.md)   
 [Identifier la source de packages à l'aide de signatures numériques](security/identify-the-source-of-packages-with-digital-signatures.md)  
  
  
