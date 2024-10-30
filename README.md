import React, { useState } from 'react';
import { Card, CardContent, CardHeader, CardTitle } from '@/components/ui/card';
import { Button } from '@/components/ui/button';
import { Recycle, Ticket, Coffee, Cookie } from 'lucide-react';

const RewardApp = () => {
  const [bottles, setBottles] = useState(0);
  
  const rewards = [
    { name: 'Entrada al Cine', cost: 50, icon: <Ticket className="w-8 h-8" /> },
    { name: 'Torta', cost: 25, icon: <Cookie className="w-8 h-8" /> },
    { name: 'Refresco', cost: 20, icon: <Coffee className="w-8 h-8" /> }
  ];

  const addBottle = () => {
    setBottles(prev => prev + 1);
  };

  const claimReward = (cost) => {
    if (bottles >= cost) {
      setBottles(prev => prev - cost);
      alert('¡Recompensa canjeada con éxito!');
    } else {
      alert('No tienes suficientes botellas para esta recompensa');
    }
  };

  return (
    <div className="max-w-md mx-auto p-4 space-y-4">
      <Card>
        <CardHeader>
          <CardTitle className="text-center text-2xl">
            EcoRecompensas
          </CardTitle>
        </CardHeader>
        <CardContent>
          <div className="text-center mb-6">
            <div className="text-4xl font-bold mb-2">{bottles}</div>
            <div className="text-gray-600">Botellas Recolectadas</div>
            <Button 
              className="mt-4 bg-green-500 hover:bg-green-600"
              onClick={addBottle}
            >
              <Recycle className="mr-2 h-4 w-4" />
              Agregar Botella
            </Button>
          </div>

          <div className="space-y-4">
            {rewards.map((reward) => (
              <Card key={reward.name} className="bg-white">
                <CardContent className="p-4">
                  <div className="flex items-center justify-between">
                    <div className="flex items-center space-x-4">
                      {reward.icon}
                      <div>
                        <div className="font-medium">{reward.name}</div>
                        <div className="text-sm text-gray-500">
                          {reward.cost} botellas
                        </div>
                      </div>
                    </div>
                    <Button
                      onClick={() => claimReward(reward.cost)}
                      disabled={bottles < reward.cost}
                      className={bottles >= reward.cost ? 'bg-blue-500 hover:bg-blue-600' : 'bg-gray-300'}
                    >
                      Canjear
                    </Button>
                  </div>
                </CardContent>
              </Card>
            ))}
          </div>
        </CardContent>
      </Card>
    </div>
  );
};

export default RewardApp;
<!---
jese2006/jese2006 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
