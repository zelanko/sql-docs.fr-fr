---
title: Provisionnement du certificat PWD
description: La page de provisionnement de certificats PDW du système Analytics Platform Configuration Manager importe ou supprime le certificat utilisé par la région PDW.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 676335fb8ee4aac5906c61084c28cd94cf8ea815
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "74400892"
---
# <a name="pdw-certificate-provisioning---analytics-platform-system"></a>Approvisionnement de certificats PDW-système de plateforme d’analyse
La page de **provisionnement de certificats PDW** du système Analytics Platform **Configuration Manager** importe ou supprime le certificat utilisé par la région PDW. À l’aide de, un certificat pour chiffrer les connexions peut aider à sécuriser la communication avec le nœud de contrôle via des clients SQL Server, des outils qui utilisent les pilotes SQL Server PDW, la [console d’administration](monitor-the-appliance-by-using-the-admin-console.md)et les charges de Integration Services.  
  
## <a name="prerequisites"></a>Prérequis  
Avant d’installer le certificat, procédez comme suit :  
  
1.  Obtenez un certificat sécurisé. Si vous avez besoin de plus d’informations sur la façon d’obtenir un certificat sécurisé, contactez Support Microsoft.  
  
2.  Enregistrez le certificat dans le nœud de contrôle d’un fichier PFX protégé par un mot de passe.  
  
## <a name="for-security-reasons-obtain-a-trusted-certificate"></a>Pour des raisons de sécurité, obtenez un certificat approuvé  
SQL Server PDW prend en charge l’utilisation d’un certificat pour chiffrer les connexions au nœud de contrôle ; y compris les connexions à la **console d’administration**.  
  
Par défaut, la **console d’administration** inclut un certificat auto-signé qui fournit la confidentialité, mais pas l’authentification du serveur. Cela peut rendre les communications vulnérables à une attaque de l’intercepteur. Lorsqu’un utilisateur se connecte à la console d’administration à l’aide du certificat auto-signé, Internet Explorer retourne l’erreur : « il y a un problème avec le certificat de sécurité de ce site Web ».  
  
Bien que la connexion via le certificat auto-signé chiffre les données en vol entre le client et le serveur, la connexion est toujours menacée par les attaquants.  
  
> [!WARNING]  
> Les administrateurs d’appliances doivent acquérir immédiatement un certificat lié à une autorité de certification approuvée reconnue par les clients, afin de disposer d’une connexion sécurisée et de supprimer l’erreur signalée par Internet Explorer.  
  
Le chemin d’accès de certification doit contenir le nom de domaine complet qui correspond à l’adresse IP de cluster du nœud de contrôle (recommandé) ou le nom que les utilisateurs tapent dans leurs barres d’adresses de navigateur pour accéder à la **console d’administration**.  
  
Utilisez le**Configuration Manager** système de plateforme d’analyse pour ajouter ou supprimer le certificat approuvé. L’utilisation directe de l’outil de configuration de certificat des services HTTP Microsoft Windows (**winHttpCertCfg. exe**) pour gérer le certificat n’est pas prise en charge.  
  
## <a name="import-or-remove-the-certificate"></a>Importer ou supprimer le certificat  
Les instructions suivantes indiquent comment importer ou supprimer le certificat de l’appareil.

> [!WARNING]
> Pour renouveler un certificat expiré, vous devez supprimer le certificat existant avant d’importer le nouveau certificat.
  
### <a name="to-import-the-certificate"></a>Pour importer le certificat  
  
1.  Lancez le **Configuration Manager**. Pour plus d’informations, consultez [la page lancement du&#41;Configuration Manager &#40;Analytics Platform System ](launch-the-configuration-manager.md).  
  
2.  Dans le volet gauche de la **Configuration Manager**, développez **topologie de Data Warehouse parallèle**, puis cliquez sur **certificats**.  
  
3.  Sélectionnez **Importer un certificat et configurez l’appliance pour l’utiliser**, puis cliquez sur **Parcourir** pour rechercher et sélectionner le fichier de certificat.  
  
4.  Entrez le mot de passe du certificat dans le champ **mot de passe** .  
  
5.  Cliquez sur **appliquer** pour configurer le certificat de l’appliance.  
  
SQL Server PDW ne chiffre pas la connexion actuelle à l’aide du certificat importé, mais utilise le certificat pour les nouvelles connexions.  
  
### <a name="to-remove-the-previously-imported-certificate"></a>Pour supprimer le certificat précédemment importé  
  
1.  Lancez le **Configuration Manager**. Pour plus d’informations, consultez [la page lancement du&#41;Configuration Manager &#40;Analytics Platform System ](launch-the-configuration-manager.md).  
  
2.  Dans le volet gauche de la **Configuration Manager**, développez **topologie de Data Warehouse parallèle**, puis cliquez sur **certificats**.  
  
3.  Sélectionnez **Supprimer tous les certificats approvisionnés dans l’appliance**.  
  
4.  Cliquez sur **appliquer** pour supprimer le certificat précédemment importé de l’appliance.  
  
SQL Server PDW continuera à chiffrer les connexions en cours, mais n’utilisera pas le certificat supprimé pour les nouvelles connexions.  
  
![Certificat PDW des appliances DWConfig](./media/pdw-certificate-provisioning/SQL_Server_PDW_DWConfig_ApplPDWCert.png "SQL_Server_PDW_DWConfig_ApplPDWCert")  
  
## <a name="see-also"></a>Voir aussi  
[Lancez le système de plateforme Configuration Manager &#40;Analytics&#41;](launch-the-configuration-manager.md)  
<!-- MISSING LINKS [HDInsight Certificate Provisioning &#40;Analytics Platform System&#41;](hdinsight-certificate-provisioning.md)  -->  
  
