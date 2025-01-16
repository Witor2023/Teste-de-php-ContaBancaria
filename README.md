<?php

class ContaBancaria{
    public $nome;
    public $dinheiro = 0;
    public $numeroConta;
    public $endereco;

    public function __construct($nome, $dinheiro, $endereco){
        $this->nome = $nome;
        $this->dinheiro = $dinheiro;
        $this->numeroConta = rand(10000, 99999) . date("Y");
        $this->endereco = $endereco;
    }

    public function transferir($valor, $outra_conta){
        // Verifica se a conta tem saldo suficiente
        if($this->dinheiro >= $valor){
            // Subtrai o valor da conta de origem
            $this->dinheiro -= $valor;
            // Adiciona o valor à conta de destino
            $outra_conta->dinheiro += $valor;
            echo "Transferência de R$ {$valor} realizada com sucesso!<br>";
        } else {
            echo "Saldo insuficiente para realizar a transferência.<br>";
        }
    }
}

// Criando as contas bancárias
$conta_witor = new ContaBancaria("Witor", 400, "Paulo Jacinto");
$conta_guilherme = new ContaBancaria("Guilherme", 0, "Raimundo Jacinto");

// Realizando a transferência
$conta_witor->transferir(100, $conta_guilherme);

echo "Saldo do Witor: R$ " . $conta_witor->dinheiro . "<br>";
echo "Saldo do Guilherme: R$ " . $conta_guilherme->dinheiro . "<br>";

?>
