<?php

namespace ListUI;

use pocketmine\Server;
use pocketmine\Player;

use jojoe77777\FormAPI\SimpleForm;

use pocketmine\command\CommandSender;
use pocketmine\command\Command;
use pocketmine\event\Listener;

use pocketmine\plugin\PluginBase;

class Ayrz extends PluginBase implements Listener{

    public function onEnable(){
        $this->getServer()->getPluginManager()->registerEvents($this, $this);
        $this->getLogger()->info("Eklenti aktif");
    }

    public function onCommand(CommandSender $p, Command $cmd, string $label, array $args): bool{
        switch ($cmd->getName()){
            case "listui":
                $this->ListForm($p);
                break;
        }
        return true;
    }

    public function ListForm($p){
        $api = $this->getServer()->getPluginManager()->getPlugin("FormAPI");
        $form = $api->createSimpleForm(function (Player $p, $data = null){
            $args = $data;
                if($args === null) return true;
        });
        $form->setTitle("Online Form");
        $form->setContent("Çevrim içi oyuncu sayısı: ".count($this->getServer()->getOnlinePlayers()));
        foreach($this->getServer()->getOnlinePlayers() as $online){
            $form->addButton($online->getName(), -1, "", $online->getName());
        }
        $form->sendToPlayer($p);
    }

}

?>
