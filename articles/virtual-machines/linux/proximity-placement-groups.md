---
title: Proximity-plaatsings groepen gebruiken
description: Meer informatie over het maken en gebruiken van proximity-plaatsings groepen voor virtuele machines in Azure.
author: cynthn
ms.service: virtual-machines
ms.topic: how-to
ms.workload: infrastructure-services
ms.date: 10/30/2019
ms.author: cynthn
ms.openlocfilehash: ee172203d6aa54b4b539356835f8a6bf2d21bad3
ms.sourcegitcommit: 829d951d5c90442a38012daaf77e86046018e5b9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/09/2020
ms.locfileid: "87288416"
---
# <a name="deploy-vms-to-proximity-placement-groups-using-azure-cli"></a>VM's implementeren op nabijheidsplaatsingsgroepen met behulp van Azure CLI

Als u virtuele machines zo dicht mogelijk wilt ophalen, moet u deze implementeren in een [proximity-plaatsings groep](co-location.md#proximity-placement-groups).

Een proximity-plaatsings groep is een logische groepering die wordt gebruikt om ervoor te zorgen dat Azure Compute-resources zich fysiek dicht bij elkaar bevinden. Proximity-plaatsings groepen zijn handig voor werk belastingen waarbij lage latentie een vereiste is.


## <a name="create-the-proximity-placement-group"></a>De plaatsings groep voor proximity maken
Maak een proximity-plaatsings groep met behulp van [`az ppg create`](/cli/azure/ppg#az-ppg-create) . 

```azurecli-interactive
az group create --name myPPGGroup --location westus
az ppg create \
   -n myPPG \
   -g myPPGGroup \
   -l westus \
   -t standard 
```

## <a name="list-proximity-placement-groups"></a>Proximity-plaatsings groepen weer geven

U kunt al uw proximity-plaatsings groepen weer geven met [AZ PPG List](/cli/azure/ppg#az-ppg-list).

```azurecli-interactive
az ppg list -o table
```

## <a name="create-a-vm"></a>Een virtuele machine maken

Maak een virtuele machine binnen de plaatsings groep met een [nieuwe AZ VM](/cli/azure/vm#az-vm-create).

```azurecli-interactive
az vm create \
   -n myVM \
   -g myPPGGroup \
   --image UbuntuLTS \
   --ppg myPPG  \
   --generate-ssh-keys \
   --size Standard_D1_v2  \
   -l westus
```

U kunt de virtuele machine weer geven in de plaatsings groep van proximity met [AZ PPG show](/cli/azure/ppg#az-ppg-show).

```azurecli-interactive
az ppg show --name myppg --resource-group myppggroup --query "virtualMachines"
```

## <a name="availability-sets"></a>Beschikbaarheidssets
U kunt ook een beschikbaarheidsset maken in de plaatsings groep voor proximity. Gebruik dezelfde `--ppg` para meter met [AZ VM Availability-set Create](/cli/azure/vm/availability-set#az-vm-availability-set-create) om een beschikbaarheidsset te maken en alle virtuele machines in de beschikbaarheidsset worden ook gemaakt in dezelfde plaatsings groep.

## <a name="scale-sets"></a>Schaalsets

U kunt ook een schaalset maken in de plaatsings groep voor proximity. Gebruik de dezelfde `--ppg` para meter met [AZ vmss Create](/cli/azure/vmss?view=azure-cli-latest#az-vmss-create) om een schaalset te maken en alle instanties worden gemaakt in dezelfde plaatsings groep.

## <a name="next-steps"></a>Volgende stappen

Meer informatie over de [Azure cli](/cli/azure/ppg) -opdrachten voor proximity placement groups.
