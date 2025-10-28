Oi
import React, { useState, useEffect } from 'react';

// ... (Ícones Printer, Sparkles, Loader2 - sem alteração)
const Printer = ({ className }) => (
  <svg
    xmlns="http://www.w3.org/2000/svg"
    width="24"
    height="24"
    viewBox="0 0 24 24"
    fill="none"
    stroke="currentColor"
    strokeWidth="2"
    strokeLinecap="round"
    strokeLinejoin="round"
    className={className}
  >
    <path d="M6 9V2h12v7" />
    <path d="M6 18H4a2 2 0 0 1-2-2v-5a2 2 0 0 1 2-2h16a2 2 0 0 1 2 2v5a2 2 0 0 1-2 2h-2" />
    <path d="M6 14h12v8H6z" />
  </svg>
);
const Sparkles = ({ className }) => (
  <svg
    xmlns="http://www.w3.org/2000/svg"
    width="24"
    height="24"
    viewBox="0 0 24 24"
    fill="none"
    stroke="currentColor"
    strokeWidth="2"
    strokeLinecap="round"
    strokeLinejoin="round"
    className={className}
  >
    <path d="m12 3-1.9 5.8-5.8 1.9 5.8 1.9 1.9 5.8 1.9-5.8 5.8-1.9-5.8-1.9z" />
    <path d="M5 21v-3" />
    <path d="M19 21v-3" />
    <path d="M3 5h3" />
    <path d="M21 5h-3" />
    <path d="M12 17.5.5 23.5" />
    <path d="M12 17.5 23.5 23.5" />
    <path d="m12 6.5-.5-5.5" />
    <path d="m12 6.5.5-5.5" />
  </svg>
);
const Loader2 = ({ className }) => (
  <svg
    xmlns="http://www.w3.org/2000/svg"
    width="24"
    height="24"
    viewBox="0 0 24 24"
    fill="none"
    stroke="currentColor"
    strokeWidth="2"
    strokeLinecap="round"
    strokeLinejoin="round"
    className={className}
  >
    <path d="M21 12a9 9 0 1 1-6.219-8.56" />
  </svg>
);

// --- NOVO ÍCONE PARA ADICIONAR ---
const PlusCircle = ({ className }) => (
  <svg
    xmlns="http://www.w3.org/2000/svg"
    width="24"
    height="24"
    viewBox="0 0 24 24"
    fill="none"
    stroke="currentColor"
    strokeWidth="2"
    strokeLinecap="round"
    strokeLinejoin="round"
    className={className}
  >
    <circle cx="12" cy="12" r="10" />
    <line x1="12" y1="8" x2="12" y2="16" />
    <line x1="8" y1="12" x2="16" y2="12" />
  </svg>
);


// ... (Função fetchWithBackoff - sem alteração)
async function fetchWithBackoff(url, options, retries = 3, delay = 1000) {
  try {
    const response = await fetch(url, options);
    if (!response.ok) {
      if (response.status === 429 && retries > 0) {
        // Throttled, retry with backoff
        await new Promise(resolve => setTimeout(resolve, delay));
        return fetchWithBackoff(url, options, retries - 1, delay * 2);
      }
      throw new Error(`HTTP error! status: ${response.status}`);
    }
    return response;
  } catch (error) {
    if (retries > 0) {
      await new Promise(resolve => setTimeout(resolve, delay));
      return fetchWithBackoff(url, options, retries - 1, delay * 2);
    }
    throw error;
  }
}

// ... (Base de dados parsedData - sem alteração)
const parsedData = [
  // ... (toda a lista de itens)
  { cod: 4921, name: 'Flv Vagem Kg' }
];

// Constante dos itens iniciais (usada para resetar)
const initialItems = parsedData.map(item => ({ ...item, weight: '' }));

export default function App() {
  const [items, setItems] = useState(initialItems);
  const [date, setDate] = useState('');
  
  // --- ESTADOS PARA API GEMINI ---
  const [analysis, setAnalysis] = useState('');
  const [isLoading, setIsLoading] = useState(false);
  const [error, setError] = useState(null);

  // --- NOVOS ESTADOS PARA ITEM TEMPORÁRIO ---
  const [tempName, setTempName] = useState('');
  const [tempWeight, setTempWeight] = useState('');

  // --- NOVO: EFEITO PARA LIMPAR APÓS IMPRESSÃO ---
  useEffect(() => {
    // Função que será chamada após a impressão
    const handleAfterPrint = () => {
      console.log("Impressão concluída. Resetando o estado...");
      
      // 1. Reseta a lista de itens para a original (limpa pesos e itens temp)
      setItems(initialItems);
      
      // 2. Limpa os outros dados da sessão
      setDate('');
      setAnalysis('');
      setError(null);
      setTempName('');
      setTempWeight('');
    };

    // Adiciona o listener
    window.addEventListener('afterprint', handleAfterPrint);

    // Remove o listener quando o componente for desmontado
    return () => {
      window.removeEventListener('afterprint', handleAfterPrint);
    };
  }, [initialItems]); // A dependência é estável, mas é bom mantê-la

  // Função para atualizar o peso de um item
  const handleWeightChange = (cod, newWeight) => {
    setItems(currentItems =>
      currentItems.map(item =>
        item.cod === cod ? { ...item, weight: newWeight } : item
      )
    );
  };

  // Função para atualizar a data
  const handleDateChange = (e) => {
    setDate(e.target.value); 
  };

  // Função para "exportar" para PDF (gatilho da limpeza)
  const handlePrint = () => {
    window.print(); // Isso vai disparar o 'afterprint' event listener
  };

  // ... (Função handleAnalyze - sem alteração)
  const handleAnalyze = async () => {
    setIsLoading(true);
    setError(null);
    setAnalysis('');

    // 1. Filtrar itens com peso
    const itemsToAnalyze = items.filter(item => parseFloat(item.weight) > 0);

    if (itemsToAnalyze.length === 0) {
      setError('Por favor, adicione o peso a pelo menos um item para analisar.');
      setIsLoading(false);
      return;
    }

    // 2. Criar o prompt
    const prompt = `Com base na lista de itens e seus pesos a seguir, gere um breve resumo nutricional (em 2-3 frases) em português. Foque nos principais benefícios de saúde. Lista: ${itemsToAnalyze
      .map(i => `${i.name} (${i.weight} Kg)`)
      .join(', ')}`;

    // 3. Chamar a API
    const apiKey = ""; // Deixe em branco, será tratado pelo ambiente
    const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-09-2025:generateContent?key=${apiKey}`;

    const payload = {
      contents: [{ parts: [{ text: prompt }] }],
    };

    try {
      const response = await fetchWithBackoff(apiUrl, {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(payload),
      });

      const result = await response.json();
      const candidate = result.candidates?.[0];

      if (candidate && candidate.content?.parts?.[0]?.text) {
        setAnalysis(candidate.content.parts[0].text);
      } else {
        throw new Error('Resposta da API inválida.');
      }
    } catch (err) {
      console.error(err);
      setError('Não foi possível gerar a análise. Tente novamente mais tarde.');
    } finally {
      setIsLoading(false);
    }
  };
  
  // --- NOVA FUNÇÃO PARA ADICIONAR ITEM TEMPORÁRIO ---
  const handleAddTempItem = (e) => {
    e.preventDefault(); // Impede o recarregamento da página
    if (!tempName) {
      alert("Por favor, insira pelo menos o nome do item."); // Simples validação
      return;
    }

    const newItem = {
      cod: `temp_${Date.now()}`, // Código único
      name: `${tempName} (Temp)`, // Marca como temporário
      weight: tempWeight || '' // Usa o peso digitado ou string vazia
    };

    // Adiciona o novo item no topo da lista
    setItems([newItem, ...items]);

    // Limpa os inputs do formulário
    setTempName('');
    setTempWeight('');
  };


  // Formata a data para exibição
  const formattedDate = date 
    ? new Date(date + 'T00:00:00').toLocaleDateString('pt-BR') 
    : '___ / ___ / ______';

  return (
    <div className="p-6 sm:p-10 max-w-5xl mx-auto font-sans bg-white rounded-xl shadow-lg print:shadow-none print:p-0">
      
      {/* --- CABEÇALHO --- */}
      {/* ... (Título, Data e Botões de Ação - sem alteração na lógica) */}
      <div className="flex flex-col sm:flex-row justify-between sm:items-center mb-6 print:mb-4">
        {/* Título e Data */}
        <div>
          <h1 className="text-3xl font-bold text-gray-800 print:text-2xl">
            Relatório de Pesagem
          </h1>
          <div className="flex items-center mt-2 space-x-2">
            <label 
              htmlFor="report-date" 
              className="text-lg font-semibold text-gray-700"
            >
              DATA:
            </label>
            <input
              id="report-date"
              type="date"
              value={date}
              onChange={handleDateChange}
              className="p-2 border border-gray-300 rounded-md print:hidden"
            />
            <span className="hidden print:block text-lg font-semibold p-2">
              {formattedDate}
            </span>
          </div>
        </div>

        {/* Botões de Ação (Exportar e Analisar) */}
        <div className="flex flex-col sm:flex-row gap-2 mt-4 sm:mt-0 print:hidden">
          <button
            onClick={handlePrint}
            className="flex items-center justify-center px-5 py-3 bg-blue-600 text-white font-semibold rounded-lg shadow-md hover:bg-blue-700 transition-colors duration-200"
          >
            <Printer className="mr-2 h-5 w-5" />
            Exportar para PDF
          </button>
          <button
            onClick={handleAnalyze}
            disabled={isLoading}
            className="flex items-center justify-center px-5 py-3 bg-gradient-to-r from-purple-500 to-pink-500 text-white font-semibold rounded-lg shadow-md hover:from-purple-600 hover:to-pink-600 transition-all duration-200 disabled:opacity-50 disabled:cursor-not-allowed"
          >
            {isLoading ? (
              <Loader2 className="mr-2 h-5 w-5 animate-spin" />
            ) : (
              <Sparkles className="mr-2 h-5 w-5" />
            )}
            {isLoading ? 'Analisando...' : '✨ Analisar Nutrientes'}
          </button>
        </div>
      </div>
      
      {/* --- NOVO: FORMULÁRIO DE ITEM TEMPORÁRIO --- */}
      <form onSubmit={handleAddTempItem} className="mb-6 p-4 bg-gray-50 border border-gray-200 rounded-lg print:hidden">
        <h3 className="text-lg font-semibold text-gray-800 mb-3">
          Adicionar Item Temporário
        </h3>
        <div className="flex flex-col sm:flex-row gap-3">
          <div className="flex-1">
            <label htmlFor="temp-name" className="block text-sm font-medium text-gray-700 mb-1">
              Nome do Item
            </label>
            <input
              type="text"
              id="temp-name"
              value={tempName}
              onChange={(e) => setTempName(e.target.value)}
              className="p-2 border border-gray-300 rounded-md w-full"
              placeholder="Ex: Uva Importada Especial"
            />
          </div>
          <div className="w-full sm:w-1/3">
            <label htmlFor="temp-weight" className="block text-sm font-medium text-gray-700 mb-1">
              Peso (Opcional)
            </label>
            <input
              type="number"
              id="temp-weight"
              step="0.01"
              value={tempWeight}
              onChange={(e) => setTempWeight(e.target.value)}
              className="p-2 border border-gray-300 rounded-md w-full"
              placeholder="0.00"
            />
          </div>
          <button
            type="submit"
            className="flex items-center justify-center px-4 py-2 bg-green-600 text-white font-semibold rounded-lg shadow-md hover:bg-green-700 transition-colors duration-200 sm:self-end"
          >
            <PlusCircle className="mr-2 h-5 w-5" />
            Adicionar
          </button>
        </div>
      </form>


      {/* --- SEÇÃO DE ANÁLISE GEMINI --- */}
      {/* ... (sem alteração) */}
      <div className="my-6 print:hidden">
        {error && (
          <div className="p-4 bg-red-50 border border-red-200 text-red-700 rounded-lg">
            <p className="font-semibold">Erro</p>
            <p>{error}</p>
          </div>
        )}
        {analysis && (
          <div className="p-4 bg-gray-50 border border-gray-200 rounded-lg shadow-sm">
            <h3 className="text-lg font-semibold text-gray-800 mb-2">
              Análise Nutricional ✨
            </h3>
            <p className="text-gray-700 whitespace-pre-wrap">{analysis}</p>
          </div>
        )}
      </div>

      {/* --- TABELA DE ITENS --- */}
      {/* ... (sem alteração) */}
      <div className="overflow-x-auto">
        <table className="w-full min-w-[600px] border-collapse">
          <thead>
            <tr className="bg-gray-100 print:bg-white border-b-2 border-gray-700">
              <th className="p-3 text-left text-sm font-bold text-gray-600 uppercase tracking-wider w-[100px]">
                Cód
              </th>
              <th className="p-3 text-left text-sm font-bold text-gray-600 uppercase tracking-wider">
                Item
              </th>
              <th className="p-3 text-left text-sm font-bold text-gray-600 uppercase tracking-wider w-[150px]">
                Peso (Kg/Un)
              </th>
            </tr>
          </thead>

          <tbody>
            {items.map((item) => (
              <tr key={item.cod} className="border-b border-gray-200 hover:bg-gray-50 print:hover:bg-white">
                <td className="p-3 text-gray-700 font-medium">
                  {item.cod}
                </td>
                <td className="p-3 text-gray-900">
                  {item.name}
                </td>
                <td className="p-3">
                  <input
                    type="number"
                    step="0.01"
                    value={item.weight}
                    onChange={(e) => handleWeightChange(item.cod, e.target.value)}
                    className="p-2 border border-gray-300 rounded-md w-full print:hidden"
                    placeholder="0.00"
                  />
                  <span className="hidden print:block p-2 text-gray-900">
                    {parseFloat(item.weight) > 0 ? parseFloat(item.weight).toFixed(2) : '0.00'}
                  </span>
                </td>
              </tr>
            ))}
          </tbody>
        </table>
      </div>
    </div>
  );
}