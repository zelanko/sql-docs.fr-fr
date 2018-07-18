---
title: Gestionnaire de connexions SAP BW | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 06b166a1-a9df-48ea-a0e8-9b8d6979c0a1
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a541988192c0233426a8f08a79743b822d3f3709
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37223756"
---
# <a name="sap-bw-connection-manager"></a>Gestionnaire de connexions SAP BW
  Le gestionnaire de connexions SAP BW est le composant de gestionnaire de connexions de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 pour SAP BW. Ainsi, le gestionnaire de connexions SAP BW fournit la connectivité à un système SAP Netweaver BW version 7 dont ont besoin les composants source et de destination de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 pour SAP BW. (La source et la destination SAP BW qui font partie du package [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 pour SAP BW sont les seuls composants [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui utilisent le gestionnaire de connexions SAP BW.)  
  
> [!IMPORTANT]  
>  La documentation de Microsoft Connector 1.1 pour SAP BW suppose que vous êtes familiarisé avec l'environnement SAP Netweaver BW. Pour plus d'informations sur SAP Netweaver BW, ou sur la configuration des objets et des processus SAP Netweaver BW objets, consultez la documentation SAP.  
  
 Lorsque vous ajoutez un gestionnaire de connexions SAP BW à un package, le `ConnectionManagerType` propriété du Gestionnaire de connexions est définie sur `SAPBI`.  
  
## <a name="configuring-the-sap-bw-connection-manager"></a>Configuration du gestionnaire de connexions SAP BW  
 Vous pouvez configurer le gestionnaire de connexions SAP BW de plusieurs manières :  
  
-   Fournissez le client, le nom d'utilisateur, le mot de passe et la langue pour la connexion.  
  
-   Déterminez si la connexion doit être établie à un serveur d'applications unique ou à un groupe de serveurs à charge équilibrée.  
  
-   Fournissez le numéro d'hôte et du système pour un serveur d'applications unique, ou fournissez le serveur de messages, le groupe et le SID pour un groupe de serveurs à charge équilibrée.  
  
-   Activez la journalisation personnalisée des appels de fonction RFC pour les composants de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 pour SAP BW. (Cette journalisation diffère de la journalisation facultative que vous pouvez activer sur les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].) Pour activer la journalisation des appels de fonction RFC, spécifiez un répertoire dans lequel stocker les fichiers journaux qui sont créés avant et après chaque appel de fonction RFC. (Cette fonctionnalité de journalisation crée un grand nombre de fichiers journaux au format XML. Comme ces fichiers journaux contiennent également toutes les lignes de données qui sont transférées, ils peuvent occuper beaucoup d'espace sur le disque.) Si vous ne sélectionnez pas de répertoire de journal, la journalisation n'est pas activée.  
  
    > [!IMPORTANT]  
    >  Si les données qui sont transférées contiennent des informations sensibles, les fichiers journaux contiendront également ces informations sensibles.  
  
-   Utilisez les valeurs que vous avez entrées pour tester la connexion.  
  
 Si vous ne connaissez pas toutes les valeurs requises pour configurer le gestionnaire de connexions, adressez-vous à votre administrateur SAP.  
  
 Pour obtenir la procédure pas à pas qui montre comment configurer et utiliser le gestionnaire de connexions, la source et la destination SAP BW, consultez le livre blanc [Utilisation de SQL Server 2008 Integration Services avec SAP BI 7.0](http://go.microsoft.com/fwlink/?LinkID=137090). Ce livre blanc explique également comment configurer les objets nécessaires dans SAP BW.  
  
### <a name="using-the-ssis-designer-to-configure-the-source"></a>Utilisation du concepteur SSIS pour configurer la source  
 Pour plus d'informations sur les propriétés du gestionnaire de connexions SAP BW que vous pouvez définir dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Éditeur du gestionnaire de connexions SAP BW](../sap-bw-connection-manager-editor.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Composants de Microsoft Connector 1.1 pour SAP BW](../microsoft-connector-for-sap-bw-components.md)  
  
  
