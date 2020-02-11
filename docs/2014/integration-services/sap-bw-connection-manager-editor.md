---
title: Éditeur du gestionnaire de connexions SAP BW | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ec970319-e749-4753-8675-9cf76ed99669
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 0da11d8f49c1de88297a9bf8876588c8b5aeb81b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66056280"
---
# <a name="sap-bw-connection-manager-editor"></a>Éditeur du gestionnaire de connexions SAP BW
  Utilisez l' **Éditeur du gestionnaire de connexions SAP BW** pour spécifier les propriétés à utiliser pour se connecter à un système SAP Netweaver BW version 7.  
  
 Le gestionnaire de connexions SAP BW fournit la connectivité à un système SAP Netweaver BW version 7 en vue d'une utilisation par la source ou la destination SAP BW. Pour en savoir plus sur le gestionnaire de connexions SAP BW de [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 pour SAP BW, consultez [Gestionnaire de connexions SAP BW](connection-manager/sap-bw-connection-manager.md).  
  
> [!IMPORTANT]  
>  La documentation de Microsoft Connector 1.1 pour SAP BW suppose que vous êtes familiarisé avec l'environnement SAP Netweaver BW. Pour plus d'informations sur SAP Netweaver BW, ou sur la configuration des objets et des processus SAP Netweaver BW objets, consultez la documentation SAP.  
  
 **Pour ouvrir l'Éditeur du gestionnaire de connexions SAP BW**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] qui contient le gestionnaire de connexions SAP BW.  
  
2.  Dans la zone Gestionnaires de connexions de l'onglet **Flux de contrôle** , procédez de l'une des façons suivantes :  
  
    -   Double-cliquez sur le gestionnaire de connexions SAP BW.  
  
         -ou-  
  
    -   Cliquez avec le bouton droit sur le gestionnaire de connexions SAP BW, puis sélectionnez **Modifier**.  
  
## <a name="options"></a>Options  
  
> [!NOTE]  
>  Si vous ne connaissez pas toutes les valeurs requises pour configurer le gestionnaire de connexions, adressez-vous à votre administrateur SAP.  
  
 **Client**  
 Spécifiez le numéro de client du système.  
  
 **Langage**  
 Spécifiez la langue utilisée par le système. Par exemple, spécifiez **FR** pour le français.  
  
 **Nom d'utilisateur**  
 Spécifiez le nom d'utilisateur qui sera utilisé pour se connecter au système.  
  
 **Mot de passe**  
 Spécifiez le mot de passe qui sera utilisé avec le nom d'utilisateur.  
  
 **Utiliser le serveur d'applications unique**  
 Connectez-vous à un serveur d'applications unique.  
  
 Pour vous connecter à un groupe de serveurs à charge équilibrée, utilisez plutôt l’option **Utiliser l’équilibrage de charge** .  
  
 **Hôte**  
 Si vous vous connectez à un serveur d'applications unique, spécifiez le nom d'hôte.  
  
> [!NOTE]  
>  Cette option est disponible uniquement si vous avez sélectionné l’option **Utiliser le serveur d’applications unique** .  
  
 **Numéro système**  
 Si vous vous connectez à un serveur d'applications unique, spécifiez le numéro du système.  
  
> [!NOTE]  
>  Cette option est disponible uniquement si vous avez sélectionné l’option **Utiliser le serveur d’applications unique** .  
  
 **Utiliser l’équilibrage de charge**  
 Connectez-vous à un groupe de serveurs à charge équilibrée.  
  
 Pour vous connecter à un serveur d'applications unique, utilisez plutôt l'option **Utiliser le serveur d'applications unique** .  
  
 **Serveur de messages**  
 Si vous vous connectez à un groupe de serveurs à charge équilibrée, spécifiez le nom du serveur de messages.  
  
> [!NOTE]  
>  Cette option est disponible uniquement si vous avez sélectionné l’option **Utiliser l’équilibrage de charge** .  
  
 **Groupe**  
 Si vous vous connectez à un groupe de serveurs à charge équilibrée, spécifiez le nom du groupe de serveurs.  
  
> [!NOTE]  
>  Cette option est disponible uniquement si vous avez sélectionné l’option **Utiliser l’équilibrage de charge** .  
  
 **SID**  
 Si vous vous connectez à un groupe de serveurs à charge équilibrée, spécifiez l'ID système pour la connexion.  
  
> [!NOTE]  
>  Cette option est disponible uniquement si vous avez sélectionné l’option **Utiliser l’équilibrage de charge** .  
  
 **Répertoire du journal**  
 Activez la journalisation des composants de [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 pour SAP BW.  
  
 Pour activer la journalisation, spécifiez un répertoire pour les fichiers journaux qui sont créés avant et après chaque appel de fonction RFC. (Cette fonctionnalité de journalisation crée un grand nombre de fichiers journaux au format XML. Comme ces fichiers journaux contiennent également toutes les lignes de données qui sont transférées, ils peuvent occuper beaucoup d'espace sur le disque.)  
  
> [!IMPORTANT]  
>  Si les données qui sont transférées contiennent des informations sensibles, les fichiers journaux contiendront également ces informations sensibles.  
  
 Pour spécifier le répertoire du journal, vous pouvez entrer le chemin d'accès au répertoire manuellement, ou cliquer sur **Parcourir** et accéder au répertoire du journal.  
  
 Si vous ne sélectionnez pas de répertoire de journal, la journalisation n'est pas activée.  
  
 **Parcourir**  
 Parcourez l'arborescence pour sélectionner un dossier pour le répertoire du journal.  
  
 **Tester la connexion**  
 Testez la connexion à l'aide des valeurs que vous avez fournies. Après avoir cliqué sur **Tester la connexion**, un message apparaît et indique si la connexion a été établie ou si elle a échoué.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide (F1) sur Microsoft Connector 1.1 pour SAP BW](microsoft-connector-for-sap-bw-f1-help.md)  
  
  
