---
title: Définir ou modifier la méthode de connexion par défaut pour DirectQuery | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: f10d5678-d678-4251-8cce-4e30cfe15751
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f5c4e2c19fb768849c3418874b4f1a831fae858c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62746611"
---
# <a name="set-or-change-the-preferred-connection-method-for-directquery"></a>Définir ou modifier la méthode de connexion par défaut pour DirectQuery
  Lorsque vous créez un modèle à utiliser en mode DirectQuery, vous devez d'abord configurer l'environnement de conception de façon à ce qu'il prenne en charge l'utilisation de DirectQuery. Pour ce faire, consultez [activer le Mode Création DirectQuery &#40;tabulaire SSAS&#41;](tabular-models/enable-directquery-mode-in-ssdt.md).  
  
 Lorsque vous êtes prêt à déployer le modèle, vous devez définir des propriétés supplémentaires pour permettre aux utilisateurs d'accéder à votre modèle à l'aide de l'un des modes DirectQuery :  
  
-   Vous devez indiquer si les requêtes sur le modèle doivent utiliser les données en mémoire cache ou la source de données relationnelle. Vous pouvez utiliser un mode hybride ou DirectQuery uniquement.  
  
-   Si vous utilisez des partitions, vous devez indiquer quelle partition utiliser comme source de données DirectQuery.  
  
-   Vous devez définir les options d'emprunt d'identité pour les utilisateurs qui accèderont à la source de données SQL Server.  
  
 Cette procédure explique comment définir la méthode de connexion par défaut pour un modèle DirectQuery dans le concepteur. Elle décrit également comment modifier cette propriété dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] une fois que le modèle a été déployé.  
  
### <a name="to-set-the-preferred-connection-method-for-a-directquery-model"></a>Pour définir la méthode de connexion par défaut pour un modèle DirectQuery  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le fichier solution pour le modèle DirectQuery.  
  
2.  Dans Visual Studio, dans le menu de **Projet** , sélectionnez **Propriétés**.  
  
3.  Dans le volet **Propriétés** , modifiez la propriété, **DirectQueryMode**, en l'une des valeurs qui prennent en charge l'utilisation de DirectQuery :  
  
    -   **InMemory avec DirectQuery**: Si vous utilisez cette option, le modèle est déployé, mais vous devez traiter le cache avant de pouvoir exécuter des requêtes sur le modèle.  
  
    -   **DirectQuery avec InMemory**: Si vous utilisez cette option, le cache sera disponible pour une utilisation par les clients s’il a déjà été traité. Si vous déployez le modèle avec ce paramètre et ne traitez pas le cache, certains clients doivent obtenir une erreur lors de la tentative de connexion au modèle.  
  
    -   **DirectQuery uniquement**: Si vous utilisez cette option, les métadonnées sont déployées mais le modèle ne comporte aucune donnée. Les clients qui tentent de se connecter à l'aide du mode en mémoire obtiennent une erreur, indiquant que le modèle n'existe pas ou n'a pas été traité.  
  
4.  En cas de erreurs, dans Visual Studio, ouvrez la **Liste d'erreurs** et résolvez tous les problèmes qui empêcheraient le modèle d'être déployé en mode DirectQuery.  
  
### <a name="to-verify-or-change-the-preferred-connection-method-for-a-directquery-model"></a>Pour vérifier ou modifier la méthode de connexion par défaut pour un modèle DirectQuery  
  
1.  Dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], connectez -vous à l'instance où vous avez déployé le modèle DirectQuery.  
  
2.  Cliquez avec le bouton droit sur la base de données model et sélectionnez **Propriétés**.  
  
3.  Dans le volet **Propriétés** , modifiez la propriété, **DirectQueryMode**, en l'une des valeurs suivantes :  
  
    -   **DirectQuery uniquement**  
  
    -   **InMemory avec DirectQuery**  
  
    -   **DirectQuery avec InMemory**  
  
 Notez que ces propriétés sont les mêmes que les propriétés que vous définissez sur le projet avant son déploiement dans Visual Studio. Vous pouvez modifier le mode de connexion par défaut pour le mode DirectQuery à tout moment, à condition d'avoir configuré le modèle de façon à ce qu'il prenne en charge l'utilisation de DirectQuery.  
  
## <a name="see-also"></a>Voir aussi  
 [Mode DirectQuery &#40;SSAS Tabulaire&#41;](tabular-models/directquery-mode-ssas-tabular.md)   
 [Activer le Mode Création DirectQuery &#40;SSAS tabulaire&#41;](tabular-models/enable-directquery-mode-in-ssdt.md)  
  
  
