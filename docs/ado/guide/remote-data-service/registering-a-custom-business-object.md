---
title: L’inscription d’un objet métier personnalisé | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- custom business object in RDS [ADO]
- registering custom business objects in RDS [ADO]
- business objects in RDS [ADO]
ms.assetid: e9032ad8-d14c-42e3-ba13-cb5f00084a79
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9db18a572fc82b05e75fb7bb286afb572fe500fd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704235"
---
# <a name="registering-a-custom-business-object"></a>Inscription d’un objet métier personnalisé
Pour permettre l’exécution d’un objet métier personnalisé (.dll ou .exe) via le serveur Web, ProgID de l’objet métier doit être entrée dans le Registre, comme expliqué dans cette procédure. Cette fonctionnalité RDS protège la sécurité de votre serveur Web en exécutant uniquement les exécutables approuvés.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
> [!NOTE]
>  Pour MDAC 2.0 et versions ultérieures et Windows DAC, l’objet métier par défaut, [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md), n’est pas enregistré par défaut pendant l’installation de MDAC/Windows DAC. Toutefois, si **RDSServer.DataFactory** a été inscrite comme sécurisés pour l’exécution sur l’ordinateur avant l’installation, l’entrée de Registre est conservée pour la nouvelle installation.  
  
### <a name="to-register-a-custom-business-object"></a>Pour inscrire un objet métier personnalisé :  
  
1.  Cliquez sur **Démarrer** puis cliquez sur **exécuter**.  
  
2.  Type **RegEdit** et cliquez sur **OK**.  
  
3.  Dans l’Éditeur du Registre, accédez à la **HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\W3SVC\Parameters\ADCLaunch** clé de Registre.  
  
4.  Sélectionnez le **ADCLaunch** clé, puis dans le **modifier**menu, pointez sur **New** et cliquez sur **clé**.  
  
5.  Tapez le ProgID de votre objet métier personnalisé, cliquez sur **entrée**. Laissez le **valeur** entrée vide.


