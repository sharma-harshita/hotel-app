import { useEffect, useState } from 'react';
import './App.css';
import { getHotelsData } from './service/service';
import Card from './Card';

function App() {

  const [hotels, setHotels] = useState(null);

  const setHotelData = async() => {
    const data = await getHotelsData();
    setHotels(data.data);
  }

  useEffect(()=>{
    setHotelData();
  },[])

  return (
    <div className="App">
      <h1>Hello World!!</h1>
      {hotels.map((value,index)=>{
        return(
          <div key={value.id}>
            <Card title={value.address} price={value.pricePerNight}/>
          </div>
        )
      })
      }
    </div>
  );
}

export default App;

















import axios from 'axios';

export const getHotelsData = () => {
    return axios.get("https://hotels-api-4ltr.onrender.com/api/hotels");
}
