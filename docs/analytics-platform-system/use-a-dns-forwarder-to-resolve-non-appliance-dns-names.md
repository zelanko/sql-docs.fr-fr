---
title: Utiliser un redirecteur DNS
description: Utilisez un redirecteur DNS pour résoudre les noms DNS non-Appliance dans Analytics Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 3d1d0d9428138da615fad7ff5745c758d9fcd3b8
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "74399431"
---
# <a name="use-a-dns-forwarder-to-resolve-non-appliance-dns-names-in-analytics-platform-system"></a>Utiliser un redirecteur DNS pour résoudre les noms DNS non-Appliance dans Analytics Platform System
Un redirecteur DNS peut être configuré sur les nœuds Active Directory Domain Services (**_ \_ domaine d’appliance_-ad01** et ** _ \_ domaine d’appliance_-AD02**) de votre appliance Analytics Platform System pour permettre aux scripts et aux applications logicielles d’accéder aux serveurs externes.  
  
## <a name="using-a-dns-forwarder"></a><a name="ResolveDNS"></a>Utilisation d’un redirecteur DNS  
L’appliance Analytics Platform System est configurée pour empêcher la résolution des noms DNS des serveurs qui ne sont pas dans l’appliance. Certains processus, tels que Windows Software Update Services (WSUS), devront accéder aux serveurs en dehors de l’appliance. Pour prendre en charge ce scénario d’utilisation, le système DNS de la plateforme d’analyse peut être configuré pour prendre en charge un redirecteur de nom externe qui permet aux ordinateurs hôtes du système de plateforme d’analyse et aux machines virtuelles d’utiliser des serveurs DNS externes pour résoudre les noms en dehors de l’appliance. La configuration personnalisée des suffixes DNS n’est pas prise en charge, ce qui signifie que vous devez utiliser des noms de domaine complets pour résoudre le nom d’un serveur non-appareil.  
  
**Pour créer un redirecteur DNS avec l’interface utilisateur graphique DNS**  
  
1.  Connectez-vous au nœud ** _ \_ domaine du dispositif_-ad01** .  
  
2.  Ouvrez le Gestionnaire DNS (**dnsmgmt. msc**).  
  
3.  Cliquez avec le bouton droit sur le nom du serveur, puis cliquez sur **Propriétés**.  
  
4.  Dans l’onglet **avancé** , désélectionnez l’option **désactiver la récursivité (désactive également les redirecteurs)** , puis cliquez sur **appliquer**.)  
  
5.  Cliquez sur l’onglet **redirecteurs** , puis sur **modifier**.  
  
6.  Entrez l’adresse IP du serveur DNS externe qui fournira la résolution de noms. Les machines virtuelles et les serveurs (hôtes) de l’appliance se connectent aux serveurs externes à l’aide de noms de domaine complets.  
  
7.  Répétez les étapes 1-6 sur le ** _ \_ domaine_de l’appliance-nœud AD02**  
  
**Pour créer un redirecteur DNS à l’aide de Windows PowerShell**  
  
1.  Connectez-vous au nœud ** _ \_ domaine du dispositif_-ad01**.  
  
2.  Exécutez le script Windows PowerShell suivant à partir du nœud ** _ \_ domaine_de l’appliance-ad01** . Avant d’exécuter le script Windows PowerShell, remplacez les adresses IP par les adresses IP de vos serveurs DNS non-appliance.  
  
    ```  
    $DNS=Get-WmiObject -class "MicrosoftDNS_Server"  -Namespace "root\microsoftdns"  
    $DNS.Forwarders = ("xxx.xxx.xxx.xxx", "xxx.xxx.xxx.xxx")  
    $DNS.put()  
    ```  
  
3.  Exécutez la même commande sur le nœud ** _ \_ Domain_-AD02** de l’appliance.  
  
## <a name="configuring-dns-resolution-for-wsus"></a>Configuration de la résolution DNS pour WSUS  
SQL Server PDW 2012 offre des fonctionnalités de maintenance et de mise à jour corrective intégrées. SQL Server PDW utilise Microsoft Update et d’autres technologies de maintenance Microsoft. Pour activer les mises à jour, l’appliance doit être en mesure de se connecter à un référentiel WSUS d’entreprise ou au référentiel Microsoft public WSUS.  
  
Pour les clients qui choisissent de configurer l’appliance pour rechercher des mises à jour sur le référentiel Microsoft public WSUS, les instructions suivantes définissent les détails de configuration appropriés sur l’appliance.  
  
> [!NOTE]  
> L’administrateur réseau du client doit fournir l’adresse IP d’un serveur DNS d’entreprise capable de résoudre les noms sur **Microsoft.com**.  
  
1.  À l’aide du Bureau à distance, connectez-vous à la machine virtuelle VMM ( <fabric domain> -VMM) à l’aide du compte d’administrateur de domaine de la structure.  
  
2.  Ouvrez le panneau de configuration, cliquez sur **réseau et Internet**, puis sur **Centre réseau et partage**.  
  
3.  Dans la liste connexion, cliquez sur **VMSEthernet**, puis sur **Propriétés**.  
  
4.  Sélectionnez **Protocole Internet version 4 (TCP/IPv4)**, puis cliquez sur **Propriétés**.  
  
5.  Dans la zone **serveur DNS auxiliaire** , ajoutez l’adresse IP fournie par l’administrateur réseau du client.  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
